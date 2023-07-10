pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t pujaray/python-jenkins:v1 .'
      }
    }
    stage('Login') {
      steps {
        sh 'echo dckr_pat_DrLDeBV2X27KhckR5MNE79D-ku0 | docker login -u pujaray --password-stdin'
      }
    }
    stage('Push') {
      steps {
        sh 'docker push pujaray/python-jenkins:v1'
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}