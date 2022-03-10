pipeline {
	//agent any
	agent { docker { image 'maven'}}
	stages {
		stage('Build') {
			steps {
				sh 'mvn --version'
				echo "Build"
			}
		}
		stage('Test') {
			steps {
				echo "Test"
			}
		}
		stage('Integration Test') {
			steps {
				echo "Integration Test"
			}
		}
	}
	post {
		always {
			echo "Always Run"
		}
		success {
			echo "Successful Run"
		}
		failure {
			echo "Failed Run"
		}
	}
}
