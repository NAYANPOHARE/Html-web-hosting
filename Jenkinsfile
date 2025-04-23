pipeline {
    agent any
    stages {
        stage('Clone Code') {
            steps {
                git 'https://github.com/your-user/your-repo.git'
            }
        }
        stage('Code Quality') {
            steps {
                withSonarQubeEnv('MySonarQubeServer') {
                    sh 'sonar-scanner -Dsonar.projectKey=html-page -Dsonar.sources=. -Dsonar.language=html'
                }
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t html-page .'
            }
        }
        stage('Run HTML App') {
            steps {
                sh 'docker run -d -p 80:80 html-page'
            }
        }
    }
}
