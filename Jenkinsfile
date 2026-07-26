pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/rohanengineeringpathx/pyproject.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'pytest'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-demo .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop flask-demo || true
                docker rm flask-demo || true
                docker run -d -p 10000:10000 --name flask-demo flask-demo
                '''
            }
        }

    }
}
