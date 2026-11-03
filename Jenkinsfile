
pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                bat '''
                where docker
                docker --version
                docker build -t portfolio .
                '''
            }
        }

        stage('Run Docker Container') {
            steps {
                bat '''
                docker rm -f portfolio-container >nul 2>&1
                docker run -d -p 8081:80 --name portfolio-container portfolio
                '''
            }
        }

        stage('Verify the Docker Container') {
            steps {
                bat 'docker ps'
            }
        }
    }
}
