pipeline {
  agent any
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