pipeline {
    agent any
    tools {
        gradle 'gradle'
        git 'git'
        nodejs 'nodejs'
    }
    environment {
        RENDER_CREDENTIALS_ID = 'be10a2f6-e031-498a-9195-c982e0d0956d'
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
                withCredentials([usernamePassword(credentialsId: 'be10a2f6-e031-498a-9195-c982e0d0956d', usernameVariable: 'melisaopiyo@gmail.com', passwordVariable: 'rnd_l5fGTsli0K1IvLrTsGUjR8sV6tMu')]) {
                    sh 'render deploy --email melisaopiyo@gmail.com --token rnd_l5fGTsli0K1IvLrTsGUjR8sV6tMu'
                }
            }
        }
    }
}