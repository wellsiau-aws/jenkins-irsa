pipeline {
  agent {
    kubernetes {
      defaultContainer 'jnlp'
      yaml """
apiVersion: v1
kind: Pod
metadata:
labels:
  component: ci
spec:
  serviceAccountName: jenkins-service-account
  containers:
  - name: aws
    image: amazon/aws-cli
    command:
    - cat
    tty: true
"""
}
   }
  stages {
    stage('Test') {
      steps {
        container('aws') {
          sh "aws s3 ls"
          sh "echo test > test.txt"
          sh "echo test > test2.txt"          
        }
      }
    }
  }
}