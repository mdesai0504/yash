pipeline{
	agent any
	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub-mdesai0504')
	}

	stages {
		stage('Build') {
			steps {
				sh 'docker build -t mynginx1:latest .'
			}
		}
		stage('Login') {
			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}
		stage('Push') {
			steps {
				sh 'docker push mynginx1:latest'
			}
		}
	}
	post {
		always {
			sh 'docker logout'
		}
	}
}
