pipeline {
	//agent any
	agent { docker { image maven:eclipse-temurin}}
	stages {
		stage('Build') {
			steps {
				sh 'maven --version'
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
