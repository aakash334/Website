pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Build Stage: Preparing workspace...'
            }
        }

        stage('Test') {
            steps {
                echo 'Test Stage: Verifying source files...'
                // Ensures the index.html is actually there before trying to copy
                bat 'if exist index.html (echo "SUCCESS: index.html found") else (echo "ERROR: index.html missing" && exit 1)'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploy Stage: Syncing files to XAMPP...'
                bat '''
                @echo off
                :: 1. Ensure the destination directory exists
                if not exist "C:\\xampp\\htdocs\\Website" mkdir "C:\\xampp\\htdocs\\Website"

                :: 2. Sync files
                :: /E = Copies all subdirectories (including empty ones)
                :: /H = Copies hidden and system files too
                xcopy /y /s /e /i /f /h * "C:\\xampp\\htdocs\\Website\\"
                '''
            }
        }
    }

    post {
        success {
            echo 'CI/CD Pipeline finished successfully! Check http://localhost/Website'
        }
        failure {
            echo 'Pipeline FAILED. Check the Console Output for errors.'
        }
    }
}
