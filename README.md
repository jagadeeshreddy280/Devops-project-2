# Devops-project-2
Deploy an Application on EKS using CI/CD

pre-requisite:-
---
cloud platform : AWS(IAM,EKS,VPC)
SCM : Github
CI/CD : Jenkins
Container platform : DockerHub

jenkins installation:
---
ubuntu ec2: https://pkg.jenkins.io/debian-stable/

linux ec2: https://www.jenkins.io/doc/tutorials/tutorial-for-installing-jenkins-on-AWS/

java Need to Install:
---
sudo apt-get update

sudo apt install openjdk-11-jdk

java --version

sudo mkdir jenkins

sudo chmod 777 -R jenkins

opening jenkins web
---
localhost:8080

Trigger jenkins job automatically whenever any changes in GitHub:-
---
IN GITHUB:

Go to repository

Inside repo --> settings -->click webhooks -->click add webhooks

Copy Jenkins url like http://2.33.344.44:8080 and Add /github-webhook/

Example: http://35.154.114.196:8080/github-webhook/

Add in Payload URL --> save it.

Change anything or push any file into git repo we can see job is triggered automatically.

NOTE: Save Git & Docker  in Jenkins

Go to Manage Jenkins --> Credentials --> Add New Credentials ** Need to connect Github to jenkins:

Go to settings-->developer settings-->token-->new token (tick all boxes) -->create

Copy token use as password Jenkins: ghp_Lmxn7epc

