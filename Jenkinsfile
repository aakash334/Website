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
                echo 'Syncing all files to XAMPP htdocs/Website...'
                bat '''
                @echo off
                :: Create folder if it doesn't exist
                if not exist "C:\\xampp\\htdocs\\Website" (
                    mkdir "C:\\xampp\\htdocs\\Website"
                )
                
                :: xcopy flags:
                :: /S = Copies directories and subdirectories
                :: /Y = Overwrites existing files without asking
                :: /I = If destination doesn't exist, assumes it's a directory
                :: /F = Displays full source and destination filenames while copying
                
                xcopy . "C:\\xampp\\htdocs\\Website\\" /S /Y /I /F
                '''
                echo 'Deployment complete! All files synced.'
            }
        }
