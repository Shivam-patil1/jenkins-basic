pipeline {
    agent any

    tools {
        nodejs "nodejs"   // Make sure you configured NodeJS in Jenkins Global Tools
    }

    stages {
        stage('Checkout') {
            steps {
                cleanWs()
                git branch: 'main', url: 'https://github.com/YourUsername/jenkins-basic.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
        }
    }

    post {
        always {
            junit '**/junit.xml' allowEmptyResults: true
        }
        success {
            echo '✅ Build & tests passed!'
        }
        failure {
            echo '❌ Build or tests failed!'
        }
    }
}
