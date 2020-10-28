pipeline {
    agent none

    stages {
        stage('Build C#') {
            agent {
                docker { image 'sdk:3.1' }
            },
            steps {
                bat "dotnet build"
            }
        }
        stage('Test C#') {
            agent {
                docker { image 'sdk:3.1' }
            },
            steps {
                bat "dotnet test"
            }
        }
        stage('Build Typescript') {
            agent {
               docker { image 'node:14-alpine' }
            },
            steps {
                bat "cd DotnetTemplate.Web",
                bat "npm run build"

            }
        },
        stage('Lint Typescript') {
            agent {
               docker { image 'node:14-alpine' }
            },
            steps {
                bat "cd DotnetTemplate.Web",
                bat "npm run lint"

            }
        },
        stage('Test Typescript') {
            agent {
               docker { image 'node:14-alpine' }
            },
            steps {
                bat "cd DotnetTemplate.Web",
                bat "npm t"

            }
        }
    }
}