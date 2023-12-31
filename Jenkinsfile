pipeline {
    agent any

    environment {
        NODEJS_HOME = tool 'YourNodeJSInstallationName' // Replace with your NodeJS installation name
        PATH = "${NODEJS_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Build') {
            steps {
                bat 'npm run build'
            }
        }

        stage('Deploy to S3') {
            steps {
               bat "aws configure set aws_access_key_id $AWS_ACCESS_KEY_ID"
               bat "aws configure set aws_secret_access_key $AWS_SECRET_ACCESS_KEY"
               bat 'aws s3 sync build/ s3://jenkins-s3-new'
                }
            }
        }
    }

