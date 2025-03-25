node {
    def app
    agent docker { image 'node:16' }:
    stages {

        stage('Build Docker Image')
        {
                app = docker.build("myapp:v2")
                echo "Docker image build successfully"
 
        }

        stage('Push Docker Image')
        {

                docker.withRegistry('https://hub.docker.com/repositories/ashask', 'docker-creds') {
                app.push("${env.BUILD_NUMBER}")
                app.push("latest")
                echo "Docker image push successfully"
               }
     
        }      
    }
}
