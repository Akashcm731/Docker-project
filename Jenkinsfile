pipeline {
	agent any
	environment {
                ECR_URL="381491956966.dkr.ecr.us-east-1.amazonaws.com/custom"
	}
	stages {
		stage ('Checkout') {
			steps {
				git branch: 'main', url: 'https://github.com/Akashcm731/java-example_war.git'
			}
		}
		stage ('Build Stage') {
			steps {
				sh 'docker build -t ${ECR_URL}:${BUILD_NUMBER} .'
			}
		}
		stage ('Push Stage') {
			steps {
				sh 'docker push ${ECR_URL}:${BUILD_NUMBER}'
			}
		}
		stage ('Deploy Stage') {
			steps {
				sh 'docker run -d --name cont_${BUILD_NUMBER} -p 8080:8080 ${ECR_URL}:${BUILD_NUMBER}'
			}
		}
	}	
}
