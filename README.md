# CKA-Preparation
=================

How to set namespace in kubernetes:

kubectl config set-context $(kubectl config current-context) --namespace=dev

To view the pods in the all the namespaces:

kubectl get pods --all-namespaces

ResourceQuota yaml file:

apiVersion: v1
kind: ResourceQuota
metadata:
  name: pods-medium
spec:
  hard:
    requests.cpu: "10"
    requests.memory: 20Gi
    pods: "10"
    limits.cpu: "20"
    limits.memory: "40Gi"

