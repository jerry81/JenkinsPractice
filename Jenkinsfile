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
        stage('Test') {
            steps {
                echo 'Tests go here'
            }
        }
        stage('confirm Release') {
            steps {
                input 'Confirm Release to Prod'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deployment script happens now'
            }
        }
    }
    post {
        success {
          mail to: 'jerry.tann@opteyes.cn',
               subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
               body: "Something is wrong with ${env.BUILD_URL}"
        }
    }
}