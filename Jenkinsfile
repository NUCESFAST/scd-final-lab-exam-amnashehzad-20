pipeline {
    agent any
//amna shhezad 21i-1209
    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the GitHub repository
                git 'https://github.com/NUCESFAST/scd-final-lab-exam-amnashehzad-20'
            }
        }
//amna shhezad 21i-1209
        stage('Build Docker images') {
            steps {
                // Build Docker images for each service
                bat 'docker-compose build'
            }
        }
//amna shhezad 21i-1209
        stage('Login to Docker Hub') {
            steps {
                // Login to Docker Hub
                withCredentials([usernamePassword(credentialsId: '4', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    bat 'docker login -u %USERNAME% -p %PASSWORD%'
                }
            }
        }
//amna shhezad 21i-1209
        stage('Push Docker images') {
            steps {
                // Push Docker images to Docker Hub
                bat 'docker-compose push'
            }
        }
    }
}
