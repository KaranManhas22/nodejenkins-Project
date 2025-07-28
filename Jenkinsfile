pipeline {
    agent any

    environment {
        NODE_ENV = 'development'
    }
    
    tools {
        nodejs 'nodemeriha'
    }
    triggers {
        pollSCM('H/2 * * * *') // Check every 5 minutes for changes
    }
    stages {
        stage('Checkout Repository') {
            steps {
                echo 'Cloning the GitHub repository...'
                git branch: 'main', url: 'https://github.com/KaranManhas22/nodejenkins-Project.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing dependencies using Node.js 23.11.0...'
                sh 'npm install'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deployment stage (add your deploy steps here)...'
                sh 'nohup npm start & disown'
            }
        }
    }

    post {
        success {
            echo '✅ Node.js pipeline completed successfully!'
        }
        failure {
            echo '❌ Something went wrong. Please check the logs.'
        }
    }
}
