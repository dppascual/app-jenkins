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
        withDockerRegistry(credentialsId: '8106217a-130d-49e3-8b15-d705e0034241', url: '') {
          sh 'docker tag app:test dppascual/app:stable'
          sh 'docker push dppascual/app:stable'
        }
      }
    }
  }
}
