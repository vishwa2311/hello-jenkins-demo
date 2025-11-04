pipeline {
  agent any
  tools {
    // Name must match what you added in Global Tool Configuration
    nodejs 'node23'
  }
  stages {
    stage('Checkout') { steps { checkout scm } }

    stage('Build') {
      steps {
        sh 'echo Installing...'
        sh 'npm --version'
        sh 'npm install'
      }
    }

    stage('Run') {
      steps {
        // run in background so pipeline can continue; for demo only
        sh 'node server.js &'
        sh 'sleep 2'
        sh 'curl -f http://localhost:3000/health || echo "Health check failed"'
      }
    }
  }
  post {
    success { echo '✅ Build successful' }
    failure { echo '❌ Build failed' }
  }
}
