node {
    def app
    stage('Clone repository') {
        checkout scm
    }
    stage('Build image') {
       app = docker.build("nikola234/kiii_lab4")
    }
    stage('Push image') {   
        docker.withRegistry('https://registry.hub.docker.com', 'd6ed9a9c-5900-4652-96c2-ee21bfdf4722') {
            app.push("${env.BRANCH_NAME}-${env.BUILD_NUMBER}")
            app.push("${env.BRANCH_NAME}-latest")
            // signal the orchestrator that there is a new version
        }
    }
}
