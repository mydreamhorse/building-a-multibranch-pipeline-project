pipeline {    
    agent any
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                sh 'echo "building..."'
            }
        }
        stage('Test') {
            steps {
                sh 'echo "testing..."'
            }
        }
        stage('Deliver for development') {
            when {
                branch 'master' 
            }
            steps {
                sh 'echo Delivering...'
            }
        }
        stage('Deploy for production') {
            when {
                branch 'production'  
            }
            steps {
                sh 'echo Deploying...'
            }
        }   
    }
}
