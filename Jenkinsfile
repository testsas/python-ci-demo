pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo '📥 Getting code from GitHub...'
                checkout scm
            }
        }

        stage('Setup Python') {
            steps {
                echo '🐍 Checking Python version...'
                bat 'python --version'
                echo 'Installing dependencies...'
                bat 'pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                echo '🧪 Running tests...'
                bat 'pytest || exit 1'
            }
        }

        stage('Deploy / Build') {
            steps {
                echo '🚀 Build successful! (simulated deploy)'
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline completed successfully!'
        }
        failure {
            echo '❌ Pipeline failed!'
        }
    }
}
