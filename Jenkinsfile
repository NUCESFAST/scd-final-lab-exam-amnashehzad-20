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
                bat 'docker-compose build'
            }
        }

        stage('Login to Docker Hub') {
            steps {
                // Login to Docker Hub
                withCredentials([usernamePassword(credentialsId: '4', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    bat 'docker login -u %USERNAME% -p %PASSWORD%'
                }
            }
        }

        stage('Push Docker images') {
            steps {
                // Push Docker images to Docker Hub
                bat 'docker-compose push'
            }
        }
    }
}
