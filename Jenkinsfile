pipeline {
    agent any
    stages {
        stage('Build') { 
            steps {
                sh './mvnw clean compile'
                withSonarQubeEnv(installationName: 'sonar_qube') {
                    sh './mvnw sonar:sonar'
                }
            }
        }
        stage('Test') {
            steps {
                sh './mvnw test'
            }
        }
        stage('Stage') {
            steps {
                sh './mvnw package'
            }
        }
        stage('Deploy') {
            steps {
                sh './mvnw site'
                sh 'java -jar target/*.jar --server.port=8081'
            }
        }
    }
}