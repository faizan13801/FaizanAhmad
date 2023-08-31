pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout code from Git
                checkout scm
            }
        }
        
        stage('Deploy') {
            steps {
                script {
                    def renderCmd = isUnix() ? 'render' : 'render.exe'
                    sh "${renderCmd} login your-render-email your-render-password"
                    sh "${renderCmd} up -s myportfolio-ix7q"
                }
            }
        }
    }
}
