pipeline {
  agent {
    kubernetes {
      yaml '''
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: jnlp
    image: 'jenkins/inbound-agent:4.7-1'
    args: ['\$(JENKINS_SECRET)', '\$(JENKINS_NAME)']
    '''
  }
}
podTemplate(cloud: 'kubernetes', containers: [containerTemplate(args: '9999999', command: 'sleep', image: 'maven', livenessProbe: containerLivenessProbe(execArgs: '', failureThreshold: 0, initialDelaySeconds: 0, periodSeconds: 0, successThreshold: 0, timeoutSeconds: 0), name: 'maven', resourceLimitCpu: '', resourceLimitEphemeralStorage: '', resourceLimitMemory: '', resourceRequestCpu: '', resourceRequestEphemeralStorage: '', resourceRequestMemory: '', workingDir: '/home/jenkins/agent')], label: 'MAVEN', name: 'maven') 
  node(MAVEN) {
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
  }  
}