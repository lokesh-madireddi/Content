1. Install Java

sudo apt update
sudo apt install openjdk-17-jre

3. Install jenkins 
curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins

4. Check the properties of Jenkins 
  ps -ef | grep jenkins 

5. To get the initial password of Jenkins use command 
  sudo cat <path from jenkins>

6. Use Docker as Agent in Jenkins Project setup and we found this useful in terms od cost/ efficiency and for spinning up and dropping down the containers.
7. Install Docker as well. 
8. Grant Jenkins user and Ubuntu user permission to docker deamon.
  sudo su - 
  usermod -aG docker jenkins
  usermod -aG docker ubuntu
  systemctl restart docker

9. To switch to jenkins 
  su - jenkins 

10. check jenkin user able to run Docker or not 
   docker run hello-world 

11. 
