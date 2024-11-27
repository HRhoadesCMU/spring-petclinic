pipeline {
    agent any
    stages {
        stage('Build') { 
            steps {
                sh 'mvnw package'
            }
        }
        stage('Run') {
            steps {
                sh 'java -jar target/*.jar'
            }
        }
    }
}