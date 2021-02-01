# JenkinsPractice

## Basics

Jenkins is automation server for build, test, delivery, and deployment

Jenkins has official docker image 
docker pull jenkins/jenkins

jenkins.war installation method requires jdk 11 or 8, 13 did not work

after webpage based installation, u are suggested to add frequently used plugins

an admin user is created next

has a web GUI 

docker has virtual console

triggers when commit to main, 
trying PR

Every jenkins build must be manually triggered with scan repository now 

## notifications

slack 
post {
    success {
        slackSend channel: '#abc-def,
                  color: 'good',
                  message: 'The pipeline ${currentBuild.fullDisplayName} completed successfully'
    }
}

email 
post {
    failure {
        mail to: 'team@example.com',
             subject: '...',
             body: 'something wrong with'
    }
}
