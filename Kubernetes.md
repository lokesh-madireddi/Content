# Kubernetes

  * Service Account
      1. A default Service account will get created when created Kubernetes
      2. Roles/cluster Roles are assigned to service accounts by help of Role Binding/cluster Role Binding.
  * Deployment
      1. Deployemnt provides Scaling and Healing.
      2. Replica-set will take care of Auto Healing.
  * Service Discovery
      1. Labels and Selectors comes to play.
      2. This will connect to pods based on lables and selectors not with IP Address.
      3. Environment variable configured in one pod will take care of lables and selectors.
      4. Service also allows external users to contact the application.

Kubectl actually depend on a file call kubeconfig file which contains list of clusters.

There contains CONTEXT which will tell that you to which cluster you connected to at the point of time - 
```kubectl config view``` , ```kubectl config current-context```

To switch the context - ```kubectl config use-context <Context_name>``` 

Install AWS CLI to configure the context. then ----> ```aws eks update-kubeconfig --region <region> --name <cluster_name>```
```kubectl get nodes``` ---> to check the nodes configured



