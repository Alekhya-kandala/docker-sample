pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'alekhya8/nginx-custom' // Replace with your Docker Hub repository
        DOCKER_CREDENTIALS = 'docker-hub' // Jenkins credential ID for Docker Hub
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
                      withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
                      sh "echo ${DOCKER_PASSWORD} | docker login -u ${DOCKER_USERNAME} --password-stdin"
                }
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
