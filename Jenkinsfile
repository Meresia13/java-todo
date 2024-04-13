pipeline {
    agent any
    
    stages {
        stage('Install Dependencies') {
            steps {
                script {
                    // Install Node.js dependencies using npm
                    sh 'npm install'
                }
            }
        }
        
        stage('Start Node.js Server') {
            steps {
                script {
                    // Start the Node.js server
                    sh 'node server &'
                    // The '&' at the end runs the command in the background
                    // so that the Jenkins job doesn't wait for the server to finish
                }
            }
        }
        
        stage('Deploy to Render') {
            steps {
                script {
                    // Use the Render CLI to deploy the project
                    sh 'render deploy --profile Melisa Opiyo'
                }
            }
        }
    }
}
