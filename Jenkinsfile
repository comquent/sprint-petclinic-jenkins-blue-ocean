pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
            sh 'mvn install -Dmaven.test.skip=true'
        )
      }
    }
    stage('Test & Analyse') {
        parallel(
          "Test": {
            sh 'mvn test'
          },
          "Java Doc": {
            sh 'mvn javadoc:javadoc'
            
          }
       }
    }
    stage('Report') {
      steps {
        junit 'target/**/*.xml'
        archive 'target/*.jar'
      }
    }
    stage('Deploy') {
      steps {
        echo 'deploy'
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
