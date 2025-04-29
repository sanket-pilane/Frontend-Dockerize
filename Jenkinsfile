pipeline {
  agent any

  stages {
    stage('Checkout Code') {
      steps {
        git branch:'main', url:'https://github.com/sanket-pilane/Frontend-Dockerize.git'
      }
    }

    stage('Clean node_modules') {
      steps {
        sh 'rm -rf node_modules package-lock.json'
      }
    }

    stage('Install Dependencies') {
      steps {
        sh 'npm install'
      }
    }

    stage('Build Docker Image') {
      steps {
        sh 'docker build -t sanketh/brainwave .'
      }
    }

    stage('Run Docker Container') {
      steps {
        sh 'docker run -d -p 3000:80 sanketh/brainwave'
      }
    }
  }

  post {
    always {
      cleanWs()
    }
  }
}