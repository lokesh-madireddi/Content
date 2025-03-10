1. Install Java
   ```
   sudo apt update
   sudo apt install openjdk-17-jre

2. Install jenkins
   ```
   curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee \
     /usr/share/keyrings/jenkins-keyring.asc > /dev/null
   echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
     https://pkg.jenkins.io/debian binary/ | sudo tee \
     /etc/apt/sources.list.d/jenkins.list > /dev/null
   sudo apt-get update
   sudo apt-get install jenkins

5. Check the properties of Jenkins
   ```
     ps -ef | grep jenkins 

7. To get the initial password of Jenkins use command 
  sudo cat <path from jenkins>

8. Use Docker as Agent in Jenkins Project setup and we found this useful in terms od cost/ efficiency and for spinning up and dropping down the containers.
9. Install Docker as well. 
10. Grant Jenkins user and Ubuntu user permission to docker deamon.
 
  ```
   sudo su - 
  usermod -aG docker jenkins
  usermod -aG docker ubuntu
  systemctl restart docker
   ```
11. To switch to jenkins 
  su - jenkins 

12. check jenkin user able to run Docker or not 
   docker run hello-world


If Creating any Master - Worker nodes by using Jenkins, make sure java should be installed in all the nodes 
Private key of master node should be configured in Jenkins and Public key should be configured in Worker node.

Try not to run jobs in Master Node. All the containers should run on Worked node.

"Role-Based Autherization Strategy" - Install this plugin in Jenkins to grant access to different users.
Then Manage jenkings --> Security --> Authraization "Role Based Strategy" ---> Save 
Then comes option to assign roles.


In Jenkins We have concepts like Agents, Role Based Access control, Shared Libraries.

