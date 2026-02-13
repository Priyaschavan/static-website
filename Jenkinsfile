pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/Priyaschavan/static-website.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t static-website .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker rm -f static-container || true'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 8081:80 --name static-container static-website'
            }
        }
    }
}

