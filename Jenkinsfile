pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "your-dockerhub-username/calculator-app" // Replace with your Docker Hub username and image name
        GITHUB_REPO = "https://github.com/your-username/your-repo.git" // Replace with your GitHub repository URL
    }

    stages {
        stage('Checkout Code') {
            steps {
                echo 'Cloning the GitHub repository...'
                git branch: 'main', url: "${env.GITHUB_REPO}"
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image...'
                script {
                    sh """
                    docker build -t ${env.DOCKER_IMAGE}:latest .
                    """
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                echo 'Pushing Docker image to Docker Hub...'
                script {
                    sh """
                    docker login -u ${DOCKER_USERNAME} -p ${DOCKER_PASSWORD}
                    docker push ${env.DOCKER_IMAGE}:latest
                    """
                }
            }
        }

        stage('Deploy Application') {
            steps {
                echo 'Deploying the application using Docker...'
                script {
                    sh """
                    docker run -d -p 8080:80 --name calculator-app ${env.DOCKER_IMAGE}:latest
                    """
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check the logs for more details.'
        }
    }
}
