pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  
  stages {
    stage('Build') {
      steps {
        bat 'docker build -t pujaray/python-jenkins:v1 .'
      }
    }
    stage('Login') {
      steps {
        bat 'echo dckr_pat_EHHKqtv8Pq4lq7PZJLKyiGgckJY | docker login -u pujaray --password-stdin'
      }
    }
    stage('Push') {
      steps {
        bat 'docker push pujaray/python-jenkins:v1'
      }
    }
  }
  post {
    always {
      bat 'docker logout'
    }
  }
}