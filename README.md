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
