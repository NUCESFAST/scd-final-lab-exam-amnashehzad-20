pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the GitHub repository
                git 'https://github.com/NUCESFAST/scd-final-lab-exam-amnashehzad-20'
            }
        }

        stage('Build Docker images') {
            steps {
                // Build Docker images for each service
                sh 'docker-compose build'
            }
        }

        stage('Login to Docker Hub') {
            steps {
                // Login to Docker Hub
                withCredentials([usernamePassword(credentialsId: 'dockerHubCredentials', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    sh 'docker login -u $USERNAME -p $PASSWORD'
                }
            }
        }

        stage('Push Docker images') {
            steps {
                // Push Docker images to Docker Hub
                sh 'docker-compose push'
            }
        }
    }
}