pipeline {
    agent any 

    environment {
        JAVA_HOME = '/home/ec2-user/tools/Java_8'
    }
    
    tools {
        maven 'MVN 3.3'
    }
    
    stages {
        stage('Build') { 
            steps { 
                sh "mvn install -Dmaven.test.skip=true"
            }
        }
        stage('Test'){
            steps {
                sh "mvn test"
            }
        }
        stage('Report'){
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
}
