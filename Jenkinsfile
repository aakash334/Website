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
                // Checks if index.html exists before deploying
                bat 'if exist index.html (echo File exists) else (exit 1)'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying to XAMPP htdocs...'
                // This copies your files directly to the XAMPP server
                bat 'xcopy /Y index.html C:\\xampp\\htdocs\\'
                echo 'Deployment completed! View at http://localhost/index.html'
            }
        }
    }
}
