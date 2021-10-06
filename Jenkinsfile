pipeline {
  agent {
    kubernetes {
      yaml '''
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: maven
    image: 'maven:3.8.1-jdk-8'
    args: 99d
    '''
  }
}
  stages {
    stage('Hello World') {
      steps {
        sh 'echo Hello World'
      }
    }   
    stage('Email') {
      steps {
        emailext (
          subject: "SUCCESSFUL: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
          body: """SUCCESSFUL: Job '${JOB_NAME} [${BUILD_NUMBER}]':
          Check console output at ${BUILD_URL}""",
          to: 'bilal.hussain@concanon.com'
        )
      }
    }
  }
}
