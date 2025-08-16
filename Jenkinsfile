pipeline {
    agent any
    tools { nodejs 'NodeJS 20' }

    parameters {
        booleanParam(name: 'SKIP_TEST', defaultValue: false, description: 'Skip test stage if true')
    }

    stages {
        stage('Build') {
            steps {
                echo "📦 Installing dependencies..."
                sh 'npm install'
            }
        }

        stage('Test') {
            when { expression { return !params.SKIP_TEST } }
            steps {
                echo "🧪 Running tests..."
                sh 'npm test'
            }
        }

        stage('Deploy') {
            when {
                allOf {
                    branch 'main'
                    expression { currentBuild.currentResult == 'SUCCESS' }
                }
            }
            steps {
                echo "🚀 Deploying since this is 'main' and build was successful."
                // Place your actual deployment command here
            }
        }
    }

    post {
        success { echo "✅ Pipeline completed successfully!" }
        failure { echo "❌ Pipeline failed." }
    }
}
