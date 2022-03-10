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
                bat 'mvn --version'
                bat 'docker version'
                bat 'mvn clean compile'
            }
        }
        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }
        stage('Integration Test') {
            steps {
                bat 'mvn failsafe:integration-test failsafe:verify'
            }
        }
        stage('Package') {
            steps {
                bat 'mvn package'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("ahmedsalawy/currency-exchange-devops:${env:BUILD_TAG}")
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('', 'DockerHub') {
                         dockerImage.push()
                         dockerImage.push('latest')
                    }
                }
            }
        }
    }
}
