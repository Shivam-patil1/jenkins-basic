pipeline {
    agent any

    tools {
        nodejs "NodeJS" // Make sure this matches your Jenkins NodeJS tool name
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Shivam-patil1/jenkins-basic.git'
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
            echo 'Pipeline finished!'
        }
        success {
            echo 'Tests passed ✅'
        }
        failure {
            echo 'Tests failed ❌'
        }
    }
}
