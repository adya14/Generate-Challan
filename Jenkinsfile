pipeline {
    agent any

    environment {
        PYTHON_VERSION = '3.9.1'
        IMAGE_NAME = 'your-docker-registry/your-python-app'
        DOCKERFILE_PATH = 'Dockerfile' // Adjust if your Dockerfile is in a different location
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Prepare Environment') {
            steps {
                script {
                    sh "python${PYTHON_VERSION} -m venv venv"
                    sh "source venv/bin/activate"
                }
            }
        }

        stage('Install Dependencies') {
            steps {
                sh "pip install -r requirements.txt"
            }
        }

        stage('Run Tests') {
            steps {
                sh "python -m pytest"
            }
        }

        stage('Build') {
            steps {
                script {
                    // Include any additional build steps here
                    sh "python setup.py sdist bdist_wheel"
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Build Docker image
                    sh "docker build -t ${IMAGE_NAME} -f ${DOCKERFILE_PATH} ."
                }
            }
        }

        stage('Deploy') {
            steps {
                // Add deployment steps here, if applicable
            }
        }
    }

    post {
        success {
            echo 'Build and deployment successful!'
        }

        failure {
            echo 'Build or deployment failed. Take necessary actions.'
        }

        always {
            echo 'Pipeline completed.'
        }
    }
}
