pipeline {
    agent any 

    environment {
        mvnHome = tool 'MVN 3.3'
        env.JAVA_HOME = tool 'Java 8'
    }
    
    stages {
        stage('Build') { 
            steps { 
                sh "'${mvnHome}/bin/mvn' install -Dmaven.test.skip=true"
            }
        }
        stage('Test'){
            steps {
              junit 'target/**/*.xml'
            }
        }
        stage('Deploy') {
            steps {
              echo 'deploy'
            }
        }
    }
}
