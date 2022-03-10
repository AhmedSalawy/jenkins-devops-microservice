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
                sh 'mvn --version'
                sh 'docker version'
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
        stage('Package') {
            steps {
                sh 'mvn package'
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
