pipeline {
    agent any

    stages {

       

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t vite-app .'
            }
        }

        stage('Deploy Container') {
            steps {
                bat '''
                docker stop vite-container || true
                docker rm vite-container || true
                docker run -d -p 8080:80 --name vite-container vite-app
                '''
            }
        }
    }
}
