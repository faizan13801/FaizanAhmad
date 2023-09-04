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
                // Install Render CLI within the Jenkins workspace
                script {
                    // Create a directory to store the Render CLI within the workspace
                    def renderCliDir = "${WORKSPACE}/render"
                    
                    // Download the Render CLI to the workspace directory
                    sh "curl -o ${renderCliDir}/render https://render.com/cli/latest/linux/render"
                    
                    // Make the Render CLI executable
                    sh "chmod +x ${renderCliDir}/render"
                }
                
                // Log in to Render using environment variables
                sh "render login $RENDER_EMAIL $RENDER_PASSWORD"

                // Deploy to your service
                sh 'render up -s myportfolio-ix7q'
            }
        }
        
        // Add more stages as needed for your pipeline
    }
    
    // Add post-build actions and other configurations here
}
