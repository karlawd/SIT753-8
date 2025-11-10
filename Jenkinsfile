pipeline {
    agent any

    tools {
        nodejs 'NodeJS_25.1.0'   // Must match the NodeJS installation name in Jenkins > Manage Jenkins > Tools
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/karlawd/SIT753-8.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                // Allow the pipeline to continue even if tests fail
                sh 'npm test || true'
            }
        }

        stage('Generate Coverage Report') {
            steps {
                // Run coverage script if defined in package.json
                sh 'npm run coverage || true'
            }
        }

        stage('NPM Audit (Security Scan)') {
            steps {
                // Run npm audit to detect vulnerabilities
                sh 'npm audit || true'
            }
        }
    }
}

