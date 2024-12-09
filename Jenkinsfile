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
                sh './mvnw install'
            }
        }
        stage('Deploy') {
            steps {
                withCredentials([sshUserPrivateKey(credentialsId: 'ansible_ssh', keyFileVariable: 'SSH_KEY')]) {
                    ansiblePlaybook(playbook: '/vagrant/deployment_playbook.yml', inventory: '/etc/ansible/hosts')
                }

                //sh './mvnw deploy'
                //sh './mvnw site'
                //sh 'java -jar target/*.jar --server.port=8081'
            }
        }
    }
}