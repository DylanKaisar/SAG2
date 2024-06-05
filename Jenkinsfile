pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Verify tooling') {
            steps {
                bat 'echo Verifying tooling...'
                // Add Windows-compatible commands here
            }
        }
        stage('Clear all running docker containers') {
            steps {
                bat 'docker ps -q | ForEach-Object {docker stop $_}'
                bat 'docker ps -aq | ForEach-Object {docker rm $_}'
            }
        }
        stage('Start Docker') {
            steps {
                bat 'net start docker'
            }
        }
        stage('Run Composer Install') {
            steps {
                bat 'composer install'
            }
        }
        stage('Populate .env file') {
            steps {
                bat 'copy .env.example .env'
            }
        }
        stage('Run Tests') {
            steps {
                bat 'vendor\\bin\\phpunit'
            }
        }
    }

    post {
        always {
            bat 'echo Cleanup steps...'
            // Add any cleanup steps needed
        }
        success {
            bat 'echo Build succeeded!'
        }
        failure {
            bat 'echo Build failed!'
        }
    }
}
