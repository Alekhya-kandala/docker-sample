pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'alekhya8/nginx-custom' // Replace with your Docker Hub repository
        DOCKER_CREDENTIALS = 'docker-hub-credentials' // Jenkins credential ID for Docker Hub
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the repository containing the Dockerfile
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image
                    sh "docker pull nginx"
                }
            }
        }

        stage('Login to Docker Hub') {
            steps {
                script {
                    // Log in to Docker Hub
                    sh "echo ${env.DOCKER_PASSWORD} | docker login -u ${env.DOCKER_USERNAME} --password-stdin"
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    // Push the Docker image to Docker Hub
                    sh "docker push alekhya8/nginx-custom"
                }
            }
        }
    }

}
