pipeline {
    agent any

    environment {
        MARS_APP_NAME = "smaitic-api"
        JUPITER_IMAGE_TAG = "v4"
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Validate Dockerfile') {
            steps {
                sh 'test -f app/Dockerfile'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t ${MARS_APP_NAME}:${JUPITER_IMAGE_TAG} app/'
            }
        }

        stage('Docker Image Scan') {
            steps {
                echo 'Container security scan would run here'
            }
        }

        stage('Helm Lint') {
            steps {
                sh 'helm lint helm-chart/'
            }
        }

        stage('Helm Package') {
            steps {
                sh 'helm package helm-chart/'
            }
        }

        stage('Deploy to EKS') {
            steps {
                echo 'Deployment to AWS EKS would happen here using Helm'
            }
        }
    }

    post {

        success {
            echo 'Pipeline completed successfully'
        }

        failure {
            echo 'Pipeline failed'
        }

        always {
            echo 'Pipeline execution finished'
        }
    }
}