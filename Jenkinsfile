pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t app:test .'
      }
    }
    stage('Test') {
      steps {
        echo 'Test'
        sh '/bin/nc -vz localhost 22'
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploy'
        sh 'docker tag app:test app:stable'
        sh 'docker push app:stable'
      }
    }
  }
}
