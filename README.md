# HA-jenkins-Masters
# Jenkins-HA-Masters
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
