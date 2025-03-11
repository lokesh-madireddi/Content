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

Kubectl actually depend on a file call kubeconfig file which contains list of clusters.
There contains CONTEXT which will tell that you to which cluster you connected to at the point of time
