pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning repository...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
                // Replace with actual build commands, e.g., for a Node.js app: sh 'npm install'
                echo 'Build completed.'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // Replace with actual test commands, e.g., sh 'npm test'
                echo 'Tests completed.'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                // Replace with deployment commands if applicable
                echo 'Deployment completed.'
            }
        }
    }
}
