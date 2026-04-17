pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/aakash334/Website.git'
            }
        }

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
                bat 'xcopy /E /I /Y * C:\\deploy\\website'
            }
        }
    }
}
