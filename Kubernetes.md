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

```kubectl get all``` to check all deployments/services 

To switch the context - ```kubectl config use-context <Context_name>``` 

Install AWS CLI to configure the context. then ----> ```aws eks update-kubeconfig --region <region> --name <cluster_name>```
```kubectl get nodes``` ---> to check the nodes configured

# Example of Deploy.yaml
```
---
# Source: opentelemetry-demo/templates/component.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: opentelemetry-demo-adservice
  labels:
    
    opentelemetry.io/name: opentelemetry-demo-adservice
    app.kubernetes.io/instance: opentelemetry-demo
    app.kubernetes.io/component: adservice
    app.kubernetes.io/name: opentelemetry-demo-adservice
    app.kubernetes.io/version: "1.12.0"
    app.kubernetes.io/part-of: opentelemetry-demo
spec:
  replicas: 1
  revisionHistoryLimit: 10
  selector:
    matchLabels:
      
      opentelemetry.io/name: opentelemetry-demo-adservice
  template:
    metadata:
      labels:
        
        opentelemetry.io/name: opentelemetry-demo-adservice
        app.kubernetes.io/instance: opentelemetry-demo
        app.kubernetes.io/component: adservice
        app.kubernetes.io/name: opentelemetry-demo-adservice
    spec:
      serviceAccountName: opentelemetry-demo
      containers:
        - name: adservice
          image: 'ghcr.io/open-telemetry/demo:1.12.0-adservice'
          imagePullPolicy: IfNotPresent
          ports:
            
            - containerPort: 8080
              name: service
          env:
            - name: OTEL_SERVICE_NAME
              valueFrom:
                fieldRef:
                  apiVersion: v1
                  fieldPath: metadata.labels['app.kubernetes.io/component']
            - name: OTEL_COLLECTOR_NAME
              value: 'opentelemetry-demo-otelcol'
            - name: OTEL_EXPORTER_OTLP_METRICS_TEMPORALITY_PREFERENCE
              value: cumulative
            - name: AD_SERVICE_PORT
              value: "8080"
            - name: FLAGD_HOST
              value: 'opentelemetry-demo-flagd'
            - name: FLAGD_PORT
              value: "8013"
            - name: OTEL_EXPORTER_OTLP_ENDPOINT
              value: http://$(OTEL_COLLECTOR_NAME):4318
            - name: OTEL_LOGS_EXPORTER
              value: otlp
            - name: OTEL_RESOURCE_ATTRIBUTES
              value: service.name=$(OTEL_SERVICE_NAME),service.namespace=opentelemetry-demo,service.version=1.12.0
          resources:
            limits:
              memory: 300Mi
          volumeMounts:
      volumes:
```

# Example of svc.yaml
```
---
# Source: opentelemetry-demo/templates/component.yaml
apiVersion: v1
kind: Service
metadata:
  name: opentelemetry-demo-adservice
  labels:
    opentelemetry.io/name: opentelemetry-demo-adservice
    app.kubernetes.io/instance: opentelemetry-demo
    app.kubernetes.io/component: adservice
    app.kubernetes.io/name: opentelemetry-demo-adservice
    app.kubernetes.io/version: "1.12.0"
    app.kubernetes.io/part-of: opentelemetry-demo
spec:
  type: ClusterIP
  ports:
    - port: 8080
      name: tcp-service
      targetPort: 8080
  selector:
    opentelemetry.io/name: opentelemetry-demo-adservice
```

# Configure Service account
  To configure a service account, create a serviceaccount.yaml file which have the configurations of SA. then apply by command ```kubectl apply -f serviceaccount.yaml```. To check ```kubectl get sa```. Make sure you configured this account in all your deploy.yaml files.

  Let say if you have many services then you need to run ```kubectl apply -f <service_name>/``` in all th services folders
  Or else you can merge all the deploy.yaml files into one and then you can run that file.

To check status
  ```kubectl get pods``` 
  ```kubectl get svc```


# Service Types of Kubernetes
 1. Cluster IP
 2. Node port
 3. Load Balancer - In this API will talk to Cloud control manager (CCM) talk to cloud provider(AWS) and create LB to access from external world.
    Disadvantages - It is declarative(Various features), Cost, Only cretae ALB not F5, nginx. CCM will not work if you use other than AWS.
    
    Ingress comes to play here -
       I. It can be declarative by yaml file.
    
       II. It is cost effective -  you can cretae one LB for different services
       III. If you configure nginx ingress controller, F5 ingress controller or any other ingress controller you can use respectively.
       IV. If you use any cluster which dont have any CCM, this Ingress will create external LB for you.
       V. Routing rules(Accessable only on FQDN not on IP) can be defined by using ingress.
       VI. Ingress ----> Ingress Controller ----> LB.

    
