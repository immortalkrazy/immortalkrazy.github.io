---
layout: post
title: Jenkins on AWS Instance
---
## JENKINS @ AWS
### redHat Instance
### Connect anywhere and everywhere

![](/images/aws-jenkins.png)



			---jenkins on AWS---
			 (redHat Instance)
			 
install java first it is required for jenkins
- sudo yum install java

install wget, it is not present in AWS redHat installation
- sudo yum install wget

download jenkins from jenkins site
this command will download it in the specified directory
- sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo

download the key for installation from jenkins site
- sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key

now installation of jenkins
- sudo yum install jenkins

in the brwser go to:
in the instance make port 8080 avaiable 
- http://<public ipv address of instance from AWS>:8080 

when jenkins starts for the first time cat the password from
- sudo cat /var/lib/jenkins/secrets/initialAdminPassword

you are ready to go
