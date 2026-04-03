pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'main', url: 'https://github.com/sarath3-hub/devops-java-maven.git'
            }
        }

        
stage('Build Maven Project') {
    tools {
        maven 'MAVEN_3_9_6'
    }
    steps {
        sh 'mvn clean package'

            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t java-app:latest .'
            }
        }

        
            }
        }
stage('Tag & Push to ECR') {
    steps {
        script {
            sh '''
                aws ecr get-login-password --region ap-south-1 | \
                docker login --username AWS --password-stdin 238851050082.dkr.ecr.ap-south-1.amazonaws.com

                docker tag java-app:latest 238851050082.dkr.ecr.ap-south-1.amazonaws.com/java-app:latest
                
                docker push 238851050082.dkr.ecr.ap-south-1.amazonaws.com/java-app:latest
            '''

    }
}
