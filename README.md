## Demo1 Description

  * Simple golang app to test web containers
  * Using this in conjunction with Azure Container Service and CI/CD Jenkins demo
  
## How to run
 
  ```
  docker run -d --name go-web -p 8001:8001 chzbrgr71/go-web
  
  ```
  
##  Demo2 - E-commerce Application running on Kubernetes Cluster on Any Cloud or On-premises 

# Appl details https://microservices-demo.github.io/microservices-demo/deployment/monitoring-kubernetes.html


 1) Create Kubernetes Clusters and Get the credential of kub cluster
      Azure : https://docs.microsoft.com/en-us/azure/container-service/kubernetes/container-service-kubernetes-walkthrough
      
      GCP:  https://cloud.google.com/container-engine/docs/clusters/operations
      
      AWS:  https://github.com/kubernetes/kops or 
      
            https://microservices-demo.github.io/microservices-demo/deployment/kubernetes.html
	
 2) git clone https://github.com/microservices-demo/microservices-demo.git
 
 3) Create namespace-dev.yaml file with below content   # https://kubernetes.io/docs/tasks/administer-cluster/namespaces-walkthrough/

```
 {
       "kind": "Namespace",
       "apiVersion": "v1",
       "metadata": {
       "name": "sock-shop",
       "labels": {
       "name": "sock-shop"
    }
  }
}
```
 
 4) Create Name Space called "sock-shop" on Kub Cluster 
     ```
     kubectl create -f namespace-dev.json   # Refer https://kubernetes.io/docs/tasks/administer-cluster/namespaces-walkthrough/
     ``` 
 5) Make the fron-end UI App acceseible using Public IP 
     ```
     cd deploy/kubernetes folder
     
     edit complete-demo.yaml -- to change front-end container running on Port 80 to type: LoadBalancer
     ```
     
 6) Deploy Application to Cluster 
 
    ```
    kubectl apply -f complete-demo.yaml
    ```
    
 7) kubectl get svc --namespace sock-shop
 
 8) Get the Public IP of front-end and deploy open it browser
 
 9) Optionally To deploy Prometheus & Grafana and to setup all the nice graphs that we got ready for you, simply:
	
	```
         git clone https://github.com/microservices-demo/microservices-demo.git
	 
         kubectl create -f ./deploy/kubernetes/manifests-monitoring
        ``` 
