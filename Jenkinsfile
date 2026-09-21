pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Test') {
            steps {
                sh 'python manage.py test'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build . -t todo-app'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker rm -f todo-app 2>/dev/null || true'
                sh 'docker run -d --name todo-app -p 8000:8000 todo-app'
            }
        }
    }
}
