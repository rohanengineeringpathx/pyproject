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

        stage('Run Container') {
            steps {
                bat 'docker stop flask-demo || exit 0'
                bat 'docker rm flask-demo || exit 0'
                bat 'docker run -d -p 10000:10000 --name flask-demo flask-demo'
            }
        }

    }
}
