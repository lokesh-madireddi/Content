# Kubectl

Kubectl - It is a Kubernetes command line tool which is used to interact with Kubernetes API service through terminal.
Go to Official site to install Kubectl in our VM/EC2

Here We have two versions.
client version (our laptop where we installed Kubectl) and server version (Kubernetes cluster)

# Build java microservice 

install java first 
Then run gradlew with command ``` ./gradlew installDist ``` in the same Directory
If any error check Java installed with version mentioned in the gradlew 
{This install command will do many things like 1.start gradle demon 2.install dependencies 3.perform compilation 4. build application} 
Then you will get Successed msg
``` chmod +x ./gradlew ``` this command will give you permissions to the gradlew

This run will create a build directory, check that by running ```ls -ltr``` which will create exicutable/jar files
After this create a Dockerfile for this perticular service

# Build Python based Microservice 
Create a Dockerfile based on the code.

# Docker compose
After creating many images for many services we will create a docker compose file to run all these images in a sequential way.

```docker compose up -d``` Command used to create all the containers/networks/volumes in specified order in background(-d).
```docker compose down``` Command used to delete all the containers/networks/volumes which it created previously.

# Docker vs Kubernetes
  Docker Compose is used to run multiple containers with configuration.
  Kubernetes is container orchestration platform (have advantages mentioned below)
1. Service Discovery (Docker containers are ephemeral in nature - short lived - IP change)
2. High Availability
3. load balancing
4. Integration with API Gateway
5. Disaster Recovery

 I.  Local Kubernetes Platforms - minikube, k3s, kind, k3d etc.
 II. kubeadm is used in 2 or more EC2 instances 

 # Managed Kubernetes 
  Advantages 
    1. upgrades
    2. control planes & Data planes
    3. scaling
    4. UI
    5. cost
      Providers
         1. AWS - EKS (Elastic Kubernetes service)
         2. Azure - (Azure Kubernetes service)
         3. Google - (Google Kubernetes Engine)
    




