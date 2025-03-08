# Terraform 
  Lifecycle
  1. ```terraform init```
  2. ```terraform plan```
  3. ```terraform apply```

Advantages :
1. Supports multiple cloud provider platforms 
2. It Adstracts and heavylifting for you (Takes care of interaction). Only we need to create HCL files

Terraform works on HCL(_HashiCorp Language_) files and talks to cloud platforms to create resources

*Authentication with AWS account*
Profile --> Security Credentials --> Accesskeys

_**State File Management**_ - Captures/records data in Statefile, what it created on cloud.
* State file have sensivite information (NAT, LB Details with out Mask)
* This file is saved in local(Cannot push to git due to sensitivity)
* Then comes two concepts to manage (Remote Backend, State Locking)

  **I Remote Backend**
    * Tells terraform to store statefile in _S3 Bucket_ rather storing in local or GIT
    * Can apply policy which get access to few people
    * S3 is popularly used for Remote Backend.
 
  **II State Locking**
    * If Two people making changes at same time, Locking mechanism comes into play.
    * If one applying the Terraform, the statefile will get locked.
    * DinamoDB is mostly used to lock the Statefile(statelocking resource).
  
**Modular Approach** "Eg: EKS and VPC"
    * Modules are reusable items.
    * Will have Modules folder where we have all the pre-written code for creating resources.
    * we just need to invoke the modules in out main.tf file.
    
"usually will have 3 folders main.tf(Actual code), variables,tf(variables are defined here), output.tf(To get the output of resources created)"


``` terraform destroy ``` ---> Command used to delete all the resources which are cretaed previously by terraform.
