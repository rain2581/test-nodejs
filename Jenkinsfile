pipeline {
    agent any 
    stages {
        stage('Build') { 
            steps {
                // 
               sh 'hostname'
            }
        }
        stage('Test') { 
            steps {
                //
               sh 'ls -lh' 
            }
        }
        stage('Deploy') { 
            steps {
                // 
               sh 'pwd'
               sh 'find / -name kubectl'
            }
        }
    }
}
