node('linuxmint') {
    environment {
        CI = 'true'
    }
   
    stage('Build') {
        steps {
            docker.image('node:6-alpine')..withRun('-p 3000:3000 -p 5001:5000') {
                sh 'npm install'
            }
        }
    }
    stage('Test') {
        steps {
            docker.image('node:6-alpine')..withRun('-p 3000:3000 -p 5001:5000') {
                sh './jenkins/scripts/test.sh'
            }
        }
    }
    stage('Deliver for development') {
        when {
            branch 'master' 
        }
        steps {
            
            sh './jenkins/scripts/deliver-for-development.sh'
            input message: 'Finished using the web site? (Click "Proceed" to continue)'
            sh './jenkins/scripts/kill.sh'
        }
    }
    stage('Deploy for production') {
        when {
            branch 'production'  
        }
        steps {
            sh './jenkins/scripts/deploy-for-production.sh'
            input message: 'Finished using the web site? (Click "Proceed" to continue)'
            sh './jenkins/scripts/kill.sh'
        }
    }
    
}
