pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-nginx-app:latest .'
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f k8s/'
            }
        }
        stage('Verify Deployment') {
            steps {
                sh 'kubectl rollout status deployment/my-nginx-deploy'
            }
        }
    }
    post {
        success {
            echo "Deployment successful! Access at http://my-nginx.local"
        }
    }
}