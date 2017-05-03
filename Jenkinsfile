pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'mvn install -Dmaven.test.skip=true'
      }
    }
    stage('Test') {
      steps {
        sh 'mvn test'
      }
    }
  }
  tools {
    maven 'MVN 3.3'
  }
  environment {
    JAVA_HOME = '/home/ec2-user/tools/Java_8'
  }
}