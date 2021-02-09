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

## architecture 

jenkins designed for distributed build environments 

jenkins agent - can run in parallel 
1.  controller - original node 
2.  agent - administered by agent 
    agents launched on docker image, k8s cluster, vm, physical machines 

using agents
1.  generate ssh key with ssh-keygen (associated with passcode)
2.  in jenkins dashboard, manage credentials, add credentials and fill out form for ssh key 
3.  use public docker-ssh-agent image (starts agent container)
4.  manage jenkins > manage nodes and clouds > New Node 
5.  setup agent with form
6.  launch agent 

## definitions

egrep - extended regular expressions, same as grep -e 
linux >> - redirects output to file appending output to end 
sh - the bourne shell 
VARS1="HOME=|USER=|MAIL=|LC_ALL=|LS_COLORS=|LANG=" <-- this sets a string in bash
VARS2="HOSTNAME=|PWD=|TERM=|SHLVL=|LANGUAGE=|_=" <-- sets string
VARS="${VARS1}|${VARS2}" <--sets a variable to 2 strings joined with | 
docker exec agent1 sh -c "env | egrep -v "^(${VARS})" >> /etc/environment"
  this command executes a sh command on the agent1 container that is running.  -c flag runs the command string in quotes 