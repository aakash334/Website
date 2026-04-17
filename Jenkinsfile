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
            }
        }

        stage('Deploy') {
            steps {
                bat '''
                echo Deploying files...

                if not exist C:\\deploy\\Website (
                    mkdir C:\\deploy\\Website
                )

                xcopy /E /I /Y * C:\\deploy\\Website

                echo Deployment completed!
                '''
            }
        }

    }
}
