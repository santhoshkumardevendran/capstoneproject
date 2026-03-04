pipeline {
    agent any

    stages {

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t santhoshkumardevendran/nodeapp:latest .'
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push santhoshkumardevendran/nodeapp:latest'
            }
        }

    }
}