pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build --no-cache -t vite-app .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                    # Stop and remove the container if it exists; 
                    # '|| true' ensures the pipeline doesn't fail if the container isn't there.
                    docker stop vite-container || true
                    docker rm vite-container || true
                    
                    # Run the new container
                    docker run -d -p 8081:80 --name vite-container vite-app
                '''
            }
        }
    }
}
