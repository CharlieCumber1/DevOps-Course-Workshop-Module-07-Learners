pipeline {
    agent none

    stages {
        stage('Build C#') {
            agent {
                docker { image 'sdk:3.1' }
            }
            steps {
                dotnet build
            }
        }
        stage('Test C#') {
            agent {
                docker { image 'sdk:3.1' }
            }
            steps {
                dotnet test
            }
        }
        stage('Build Typescript') {
            agent {
               docker { image 'node:14-alpine' }
            }
            steps {
                cd DotnetTemplate.Web
                npm run build

            }
        }
        stage('Lint Typescript') {
            agent {
               docker { image 'node:14-alpine' }
            }
            steps {
                cd DotnetTemplate.Web
                npm run lint

            }
        }
        stage('Test Typescript') {
            agent {
               docker { image 'node:14-alpine' }
            }
            steps {
                cd DotnetTemplate.Web
                npm t

            }
        }
    }
}