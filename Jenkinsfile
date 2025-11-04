pipeline {
    agent any

    tools {
        nodejs 'node23'  // use your NodeJS tool name from Jenkins Global Tool Config
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/vishwa2311/hello-jenkins-demo.git',
                    credentialsId: '33'
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Installing npm dependencies...'
                sh 'npm install'
            }
        }

        stage('Build App') {
            steps {
                echo 'Building application...'
                sh 'echo Build successful'
            }
        }

        stage('Run App in Background') {
            steps {
                echo 'Starting Node.js app in background...'
                sh '''
                    nohup node app.js > app.log 2>&1 &
                    echo "✅ Node.js app started on port 3000"
                '''
            }
        }
    }

    post {
        success {
            echo '✅ Build & Deployment Successful!'
            echo '🌐 Access your app at: http://35.172.199.64:3000/'
        }
        failure {
