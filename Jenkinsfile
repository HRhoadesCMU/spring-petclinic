pipeline {
    agent any
    stages {
        stage('Build') { 
            steps {
                sh './mvnw clean compile'
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
                sh './mvnw deploy'
                //sh './mvnw site'
                //sh 'java -jar target/*.jar --server.port=8081'
            }
        }
    }
}