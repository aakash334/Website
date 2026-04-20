pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building project...'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing project...'
                // Check if the source file exists in GitHub workspace
                bat 'if exist index.html (echo File exists) else (exit 1)'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying to XAMPP htdocs/Website...'
                bat '''
                @echo off
                :: Create the Website folder if it does not exist
                if not exist "C:\\xampp\\htdocs\\Website" (
                    mkdir "C:\\xampp\\htdocs\\Website"
                )
                
                :: Copy the file into that specific folder
                copy /Y index.html "C:\\xampp\\htdocs\\Website\\"
                '''
                echo 'Deployment completed!'
            }
        }
    }
}
