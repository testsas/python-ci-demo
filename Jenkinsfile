pipeline {
    agent any
    stages {
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

        stage('Deploy') {
            when {
                expression { currentBuild.resultIsBetterOrEqualTo('SUCCESS') }
            }
            steps {
                echo '🚀 Deploying application...'
                // مثال: نسخ التطبيق لمجلد الإنتاج وتشغيله
                bat '''
                mkdir C:\\deploy-folder
                copy app.py C:\\deploy-folder\\app.py /Y
                cd C:\\deploy-folder
                python app.py
                '''
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

