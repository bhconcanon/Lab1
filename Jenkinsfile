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
    command:
    - cat
    tty: true
    '''
    defaultContainer ('maven')
  }
}
  stages {
    stage('Hello World') {
      steps {
        sh 'echo Hello World'
      }
    }
  }
    post {
      success {
        emailext (
        subject: "SUCCESSFUL: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
        body: """SUCCESSFUL: Job '${JOB_NAME} [${BUILD_NUMBER}]':
        Check console output at ${BUILD_URL}""",
        to: 'bilal.hussain@concanon.com'
        )
      }
      failure {
        emailext (
        subject: "FAILURE: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
        body: """FAULURE: Job '${JOB_NAME} [${BUILD_NUMBER}]':
        Check console output at ${BUILD_URL}""",
        to: 'bilal.hussain@concanon.com'
      )
    }   
  }
}
