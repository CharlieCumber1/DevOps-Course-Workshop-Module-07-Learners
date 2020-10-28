pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                bat "dotnet build",
                echo 'Building...'
            }
        }
        stage('Test') {
            steps {
                bat "dotnet test",
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}