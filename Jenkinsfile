pipeline {
    agent any
    tools {
        git 'Default'
    }
    stages {
        stage('Declarative: Checkout SCM') {
            steps {
                checkout scm
            }
        }
        stage('Verify tooling') {
            steps {
                bat 'echo Verifying tooling...'
            }
        }
        stage('Clear all running docker containers') {
            steps {
                script {
                    powershell """
                    docker ps -q | ForEach-Object {docker stop \$_}
                    """
                }
            }
        }
        stage('Start Docker') {
            steps {
                script {
                    // Commands to start Docker
                }
            }
        }
        stage('Run Composer Install') {
            steps {
                script {
                    // Commands to run Composer install
                }
            }
        }
        stage('Populate .env file') {
            steps {
                script {
                    // Commands to populate .env file
                }
            }
        }
        stage('Run Tests') {
            steps {
                script {
                    // Commands to run tests
                }
            }
        }
    }
    post {
        always {
            bat 'echo Cleanup steps...'
            bat 'echo Build failed!'
        }
    }
}
