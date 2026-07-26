pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/rohanengineeringpathx/pyproject.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'pytest'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t flask-demo .'
            }
        }

        stage('Deploy Docker Container') {
            steps {
                bat '''
                docker stop flask-demo || exit /b 0
                docker rm flask-demo || exit /b 0
                docker run -d -p 10000:10000 --name flask-demo flask-demo
                '''
            }
        }
    }
}