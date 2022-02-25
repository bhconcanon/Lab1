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
    stage('Hello') {
      when { tag "*" }
      steps {
        sh 'echo Hello World'
        sh 'echo This job was pulled from SCM'
      }
    }
  }
}
