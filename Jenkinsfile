pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'mvn install -Dmaven.test.skip=true'
      }
    }
    stage('Test & Analyse') {
      steps {
        parallel(
          "Test": {
            sh 'mvn test'
            
          },
          "Analyse": {
            sh 'mvn findbugs:findbugs'
            sh 'mvn checkstyle:checkstyle'
            sh 'mvn pmd:pmd'
          },
          "Java Doc": {
            sh 'mvn javadoc:javadoc -Dmaven.javadoc.failOnError=false'
          }
        )
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
