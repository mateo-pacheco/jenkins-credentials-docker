pipeline {
  agent any
  stages {
    stage('Docker Build') {
      steps {
        sh "docker build -t mateo158/jenkins:${BUILD_NUMBER} ."
      }
    }
    stage('Docker Push') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'Docker', passwordVariable: 'dockerPassword', usernameVariable: 'dockerUser')]) {
          sh "docker login -u ${env.dockerUser} -p ${env.dockerPassword}"
          sh "docker push mateo158/jenkins:${BUILD_NUMBER}"
        }
      }
    }
  }
}
