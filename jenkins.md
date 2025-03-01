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
  ps -ef | grep jenkins 

6. To get the initial password of Jenkins use command 
  sudo cat <path from jenkins>

7. Use Docker as Agent in Jenkins Project setup and we found this useful in terms od cost/ efficiency and for spinning up and dropping down the containers.
8. Install Docker as well. 
9. Grant Jenkins user and Ubuntu user permission to docker deamon.
  sudo su - 
  usermod -aG docker jenkins
  usermod -aG docker ubuntu
  systemctl restart docker

10. To switch to jenkins 
  su - jenkins 

11. check jenkin user able to run Docker or not 
   docker run hello-world 

12. 
