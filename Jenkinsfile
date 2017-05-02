pipeline {
    agent any 

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
