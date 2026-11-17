pipeline {
    agent any

    environment {
        DEPLOY_DIR = 'C:\\inetpub\\wwwroot'
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Getting code from GitHub'
                git branch: 'main',
                url: 'https://github.com/Sakshii0204/jenkins-ci-cd-experimentt.git' 
            }
        }

        stage('Build') {
            steps {
                echo 'Building Web Application'
                bat 'dir'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing Web Application'
                bat 'if not exist index.html exit /b 1'
                bat 'if not exist style.css exit /b 1'
                bat 'if not exist script.js exit /b 1'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying Application'

                bat 'if not exist "%DEPLOY_DIR%" mkdir "%DEPLOY_DIR%"'

                bat 'xcopy /Y /I index.html "%DEPLOY_DIR%\\"'
                bat 'xcopy /Y /I style.css "%DEPLOY_DIR%\\"'
                bat 'xcopy /Y /I script.js "%DEPLOY_DIR%\\"'
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
        }

        failure {
            echo 'Pipeline failed! Check console output.'
        }
    }
}
