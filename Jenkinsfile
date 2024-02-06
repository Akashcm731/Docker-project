pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                script {
                    // Checkout the source code that contains the Dockerfile
                    checkout scm
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    // Build a Docker image using the Docker CLI
                    sh 'docker build -t my-docker-image .'
                }
            }
        }

        stage('Push') {
            steps {
                script {
                    // Push the image to ECR
                    sh 'docker push my-docker-image'
                    // Note: You'll need to configure AWS credentials to push to ECR
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    // Deploy the image to a Docker server as a container
                    sh 'docker run -d -p 8080:80 my-docker-image'
                    // This command will deploy the image as a container listening on port 8080
                }
            }
        }
    }
}
