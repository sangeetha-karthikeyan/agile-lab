pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/sangeetha-karthikeyan/agile-lab.git'
            }
        }

        stage('Build') {
            steps {
                bat '"C:\\Program Files\\apache-maven-3.9.14\\bin\\mvn" clean package'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t java-app .'
            }
        }

        stage('Run') {
            steps {
                bat '''
                docker stop java-container || exit 0
                docker rm java-container || exit 0
                docker run -d --name java-container java-app
                '''
            }
        }
    }
}










