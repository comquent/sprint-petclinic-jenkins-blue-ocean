pipeline {
    agent any 

    environment {
    }
    
    stages {
        stage('Build') { 
            steps { 
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
