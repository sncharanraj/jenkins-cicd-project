pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/sncharanraj/jenkins-cicd-project.git'
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t my-app .'
            }
        }

        stage('Test') {
            steps {
                sh 'echo "Running tests..."'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                docker stop my-app-container || true
                docker rm my-app-container || true
                docker run -d --name my-app-container my-app
                '''
            }
        }
    }
}
