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
        parallel(
          "Test": {
            sh 'mvn test'
            
          },
          "Inspection": {
            sh '''mvn findbugs:findbugs
mvn checkstyle:checkstyle
mvn pmd:pmd'''
            
          },
          "Documentation": {
            sh 'mvn javadoc:javadoc -Dmaven.javadoc.failOnError=false'
            
          }
        )
      }
    }
    stage('Report') {
      steps {
        junit 'target/**/*.xml'
        archiveArtifacts 'target/*.jar'
        mail(subject: 'Build and Test Complete', body: 'We are finished!', to: 'hello@comquent.de')
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploy me!'
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