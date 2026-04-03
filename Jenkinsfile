pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'main', url: 'https://github.com/sarath3-hub/devops-java-maven.git'
            }
        }

        stage('Build Maven Project') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t java-app:latest .'
            }
        }

        stage('Tag & Push to ECR') {
            steps {
                echo "We will add ECR push code after Maven + Docker build works ✅"
            }
        }
    }
}
