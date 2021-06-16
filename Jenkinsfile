node("docker") {
    docker.withRegistry('<<carnells>>', '<<carnells@mindpointgroup.com>>>') {

        git url: "<<https://github.com/ansible-lockdown/RHEL8-STIG.git>>", credentialsId: '<<carnells@mindpointgroup.com>>'

        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id

        stage "build"
        def app = docker.build "RHEL8-STIG"

        stage "publish"
        app.push 'carnells-docker'
        app.push "${commit_id}"
    }
}
