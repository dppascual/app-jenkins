pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t app:ci .'
      }
    }
    stage('Test') {
      steps {
        echo 'Test'
        sh 'docker run --rm --name app -d -p 80:80 app:ci'
        sh '/bin/nc -vz localhost 80'
      }
      post {
        always {
          sh 'docker container stop app'
        }
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploy'
        withDockerRegistry(credentialsId: 'ef00bc47-ebec-4846-bce9-d6017baa8c0e', url: '') {
          sh 'docker tag app:test dppascual/app:stable'
          sh 'docker push dppascual/app:stable'
        }
      }
    }
  }
}
