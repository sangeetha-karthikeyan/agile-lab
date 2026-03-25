pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/sangeetha-karthikeyan/agile-lab.git'
            }
        }

        stage('Build with Maven') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t java-app .'
            }
        }

        stage('Run Container') {
            steps {
                bat '''
                docker stop java-container || true
                docker rm java-container || true
                docker run -d --name java-container java-app
                '''
            }
        }
    }
}