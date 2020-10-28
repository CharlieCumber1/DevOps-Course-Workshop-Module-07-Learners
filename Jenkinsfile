pipeline {
    agent none

    environment {
        DOTNET_CLI_HOME = "/tmp/DOTNET_CLI_HOME"
    }

    stages {
        stage('Build C#') {
            agent {
                docker { image 'mcr.microsoft.com/dotnet/core/sdk:3.1' }
            }
            steps {
                sh "dotnet build"
            }
        }
        stage('Test C#') {
            agent {
                docker { image 'mcr.microsoft.com/dotnet/core/sdk:3.1' }
            }
            steps {
                sh "dotnet test"
            }
        }
        stage('Build Typescript') {
            agent {
               docker { image 'node:14-alpine' }
            }
            steps {
                sh "cd DotnetTemplate.Web"
                sh "npm run build"

            }
        }
        stage('Lint Typescript') {
            agent {
               docker { image 'node:14-alpine' }
            }
            steps {
                sh "cd DotnetTemplate.Web"
                sh "npm run lint"

            }
        }
        stage('Test Typescript') {
            agent {
               docker { image 'node:14-alpine' }
            }
            steps {
                sh "cd DotnetTemplate.Web"
                sh "npm t"

            }
        }
    }
}