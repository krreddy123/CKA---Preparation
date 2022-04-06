# CKA-Preparation
=================

How to set namespace in kubernetes:

kubectl config set-context $(kubectl config current-context) --namespace=dev

To view the pods in the all the namespaces:

kubectl get pods --all-namespaces
