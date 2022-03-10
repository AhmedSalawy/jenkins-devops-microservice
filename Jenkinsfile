pipeline {
	agent any
	//agent { docker { image 'maven'}}
	environment {
		dockerHome = tool 'Docker'
		mavenHome = tool 'Maven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
		stage('Compile') {
			steps {
				sh 'mvn clean compile'
			}
		}
		stage('Test') {
			steps {
				sh 'mvn test'
			}
		}
		stage('Integration Test') {
			steps {
				sh 'mvn failsafe:integration-test failsafe:verify'
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
