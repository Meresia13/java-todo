pipeline {
    agent any
    tools {
        gradle 'gradle'
        git 'git'
        nodejs 'nodejs'
    }
    stages {
        stage("Clone Code") {
            steps {
                git branch: 'master', url: 'https://github.com/Meresia13/java-todo.git'
            }
        }
        
        stage('Build Code') {
            steps {
                sh 'gradle build'
            }
        }
        
        stage('Test Code') {
            steps {
                sh 'gradle test'
            }
        }
        
        stage('Install Dependencies') {
            steps {
                script {
                    // Install Node.js dependencies using npm
                    sh 'npm install'
                    // Install the express module
                    sh 'npm install express --save'
                }
            }
        }
        
        stage('Start Node.js Server') {
            steps {
                script {
                    // Start the Node.js server
                    sh 'node server.js &'
                    // The '&' at the end runs the command in the background
                    // so that the Jenkins job doesn't wait for the server to finish
                }
            }
        }
        
        stage('Deploy to Render') {
            steps {
                script {
                    // Use the Render CLI to deploy the project
                    sh '/home/meresia/bin/render deploy --profile "Melisa Opiyo"'                }
            }
        }
    }
}
