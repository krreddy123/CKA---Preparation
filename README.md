# CKA-Preparation
=================

How to set namespace in kubernetes:

kubectl config set-context $(kubectl config current-context) --namespace=dev

To view the pods in the all the namespaces:

kubectl get pods --all-namespaces

ResourceQuota yaml file:
=======================

apiVersion: v1

kind: ResourceQuota

metadata:

  name: pods-medium
  
  namespace: Dev
  
spec:

  hard:
  
    requests.cpu: "10"
    
    requests.memory: 20Gi
    
    pods: "10"
    
    limits.cpu: "20"
    
    limits.memory: "40Gi"

Service yaml file:
==================
apiVersion: v1
kind: Service
metadata: 
   -name: frontend-service
spec:
  type: NodePort
  ports:
  - targetPort: 80
    port: 80
    NodePort: 300080
  selectors:
     app: my-app
     type: front-end



apiVersion: v1
kind: Service
metadata: 
  name: back-end
spec:
   type: ClusterIP
   ports:
     - targetPort: 80
       port: 80
   selectors:
      app: my-app
      type: back-end
      
      
      
      
LoadBalance Service:

apiVersion: v1

kind: Service

metadata:

   -name: frontend-service
   
spec:

  type: LoadBalancer
  
  ports:
  
  - targetPort: 80
  - port: 80
    NodePort: 300080
  selectors:
     app: my-app
     type: front-end
     
 ===========================
 Binding:
 ========
 
apiVersion: v1

kind: Binding

metadata: 

  name: nginx
  
target:

  apiVersion: v1
  
  kind: Node
  
  name: node02

=============================

Taint and Tolerations:

Taint the node:

kubectl taint nodes node-name key=value:taint-effect

What happens to the pods that do not tolerate this taint

NoSchedule | PreferNoSchedule | NoExecute

EX:

kubectl taint nodes node1 app=blue:NoSchedule

tolerations:
  
  - key: "app"
  
    operator: "Equal"
    
    value: "blue"
    
    effect: "NoSchedule"
    
    
     
