pipeline {
  agent any

  stages {
    stage('Clone') {
      steps {
        git 'https://github.com/yourname/html-website.git'
      }
    }

    stage('Build Docker Image') {
      steps {
        script {
          docker.build('html-site')
        }
      }
    }

    stage('Run Container') {
      steps {
        script {
          sh 'docker rm -f html-container || true'
          sh 'docker run -d -p 8080:80 --name html-container html-site'
        }
      }
    }
  }
}
