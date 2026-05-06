pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/paaaaaaww/perpus-app.git'
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t perpus-backend ./backend'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                docker stop perpus-container || true
                docker rm perpus-container || true
                docker run -d -p 5000:5000 --name perpus-container perpus-backend
                '''
            }
        }
    }
}