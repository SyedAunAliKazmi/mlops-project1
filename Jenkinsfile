pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/SyedAunAliKazmi/mlops-project1.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t mlops-app .'
            }
        }
        stage('Run Docker Container') {
            steps {
                sh 'docker stop mlops-container || true'
                sh 'docker rm mlops-container || true'
                sh 'docker run -d -p 80:80 --name mlops-container mlops-app'
            }
        }
        stage('Verify Deployment') {
            steps {
                sh 'docker ps | grep mlops-container'
            }
        }
    }
}
