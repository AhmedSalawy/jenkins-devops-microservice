pipeline {
	agent any
	//agent { docker { image 'maven'}}
	environment {
		dockerHome = tool 'Docker'
		mavenHome = tool 'Maven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
		stage('Build') {
			steps {
				sh 'mvn --version'
				sh 'docker version'
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
