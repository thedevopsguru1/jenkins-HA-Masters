# HA-jenkins-Masters
# Jenkins-HA-Masters
```
#!/bin/bash
sudo yum install java-11-openjdk -y
sudo yum install wget -y
sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
rpm --import https://pkg.jenkins.io/redhat/jenkins.io-2023.key
sudo yum upgrade -y
sudo yum install jenkins -y
sudo systemctl daemon-reload
sudo systemctl start jenkins
sudo systemctl enable jenkins
```
### 1- Create two Jenkins servers and install Jenkins on them
### 2- Setup EFS
###### Follow the steps of this video to setup EFS and mount it to two Jenkins masters
https://www.youtube.com/watch?v=Wa0sM4D56qQ
##### To mount the efs directly while creating ec2
https://www.youtube.com/watch?v=poh1_829tks
### 3- Create a cronjob on the standby Jenkins server
```
crontab -e
```
```
*/1 * * * * sudo systemctl restart jenkins
```
### 4- Create a load balancer with the two Jenkins servers as the target group on port 8080 
