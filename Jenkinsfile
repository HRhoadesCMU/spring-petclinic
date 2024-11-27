pipeline {
    agent any
    stages {
        stage('Build') { 
            steps {
                withSonarQubeEnv(installationName: 'sonar_qube') {
                    sh './mvnw clean compile org.sonarsource.scanner.maven:sonar-maven-plugin:6.2.1.4610:sonar'
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