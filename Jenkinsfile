pipeline {
    agent any
    
    environment {
        RENDER_EMAIL = credentials('render-email')
        RENDER_PASSWORD = credentials('render-password')
    }
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout code from Git
                checkout scm
            }
        }
        
        stage('Deploy') {
            steps {
                // Install Render CLI on the Jenkins server (if not already installed)
                sh 'sudo curl -o /usr/local/bin/render https://render.com/cli/latest/linux/render'
                sh 'sudo chmod +x /usr/local/bin/render'

                // Log in to Render using environment variables
                sh "sudo render login $RENDER_EMAIL $RENDER_PASSWORD"

                // Deploy to your service
                sh 'sudo render up -s myportfolio-ix7q'
            }
        }
    }
}
