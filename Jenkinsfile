pipeline {
    agent any

    environment {
        IMAGE_NAME = 'ashask/my-app'
        IMAGE_TAG = "${IMAGE_NAME}"
        
    }

    
    stages {

        stage('Build Docker Image')
        {
            steps
            {
                app = docker.build("myapp:v2")
                echo "Docker image build successfully"
            }
        }

        stage('Push Docker Image')
        {
            steps
            {
                docker.withRegistry('https://hub.docker.com/repositories/ashask', 'docker-creds') {
                app.push("${env.BUILD_NUMBER}")
                app.push("latest")
                echo "Docker image push successfully"
               }
            }    
        }      
    }
}
