pipeline {
  agent {
    docker { image 'node:16-alpine' }
  }

      environment {
        IMAGE_NAME = 'ashask/my-app'
        IMAGE_TAG = "${IMAGE_NAME}:${env.GIT_COMMIT}"
       
      
      }

    stages {
     stage('Login to docker hub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-creds', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                sh 'echo ${PASSWORD} | docker login -u ${USERNAME} --password-stdin'
                }
                echo 'Login successfully' 
            }
        }

        stage('Build Docker Image')
        {
            steps
            {
                sh 'docker build -t ${IMAGE_TAG} .'
                echo "Docker image build successfully"
                sh 'docker image ls'
                
            }
        }

        stage('Push Docker Image')
        {
            steps
            {
                sh 'docker push ${IMAGE_TAG}'
                echo "Docker image push successfully"
            }
        } 
    }
}
