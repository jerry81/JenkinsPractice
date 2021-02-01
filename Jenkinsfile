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
    post {
        success {
          mail to: 'jerry.tann@opteyes.cn',
               subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
               body: "Something is wrong with ${env.BUILD_URL}"
        }
    }
}