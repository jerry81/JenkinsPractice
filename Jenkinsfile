pipeline {
    agent { docker { image 'node:14-alpine' } }
    stages {
        stage('build') {
            steps {
                sh 'npm --version'
                sh 'ls'
                sh 'yarn'
                sh 'node ./index.js'
            }
        }
    }
}