pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t app .'
      }
    }
    stage('Test') {
      steps {
        echo 'Test message'
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploy message'
      }
    }
  }
}
