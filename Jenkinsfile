pipeline {
    agent any
    stages {
        stage('Clone Code') {
            steps {
                // Replace with your GitHub repository URL
                git branch: 'main', url: 'https://github.com/Ali-Amer-RGB/TwoTierFlaskApp.git'
            }
        }
        stage('Debug files') {
              steps {
                    sh 'pwd'
                    sh 'ls -la'
                    sh 'find . -maxdepth 3 -type f -iname "dockerfile*" -print'
              }            
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-app:latest .'
            }
        }
        stage('Deploy with Docker Compose') {
            steps {
                // Stop existing containers if they are running
                sh 'docker compose down || true'
                // Start the application, rebuilding the flask image
                sh 'docker compose up -d --build'
            }
        }
    }
}
