pipeline {
  agent any

  stages {
    stage('Checkout Code') {
      steps {
        git branch:'main',url:'https://github.com/sanket-pilane/Frontend-Dockerize.git'
      }
    }

    stage('Clean node_modules') {
      steps {
        bat 'npx rimraf node_modules package-lock.json'
      }
    }

    stage('Install Dependencies') {
      steps {
        bat 'npm install'
      }
    }

    stage('Build Docker Image') {
      steps {
        bat 'docker build -t sanketh/brainwave .'
      }
    }

    stage('Run Docker Container') {
      steps {
        bat 'docker run -d -p 3000:80 sanketh/brainwave'
      }
    }
  }

  post {
    always {
      cleanWs()
    }
  }
}