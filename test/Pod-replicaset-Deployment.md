---
sort: 4
---
# Pod-replicaset-Deployment.md

# Pod
A **pod** is a fundamental unit  in Kubernetes. A pod can encapsulate one or more containers. 
If a pod doesn’t respond or fail, Kubernetes will destroy and create a new one . 
Pods are ephemeral components.


# Replicaset
A ReplicaSet ensures that a specified number of pod “replicas” are running at any given time. However, a Deployment is a higher-level concept that manages ReplicaSets and provides declarative updates to pods along with a lot of other useful features. 


# Deployment
Kubernetes **deployments** are essentially just a wrapper around ReplicaSets. The ReplicaSet manages the number of running pods, and the Deployment implements features on top of that to allow rolling updates, health checks on pods, and easy roll-back of updates.
When using Deployments, you should not directly manage the ReplicaSet that is created by the Deployment. All operations that you would perform on a ReplicaSet should be performed on the Deployment instead, which then manages the process for updating the ReplicaSet. 


![deployment ](https://raw.githubusercontent.com/yaswanthvarma/kubernetes/gh-pages/images/pod-replicaset-deployment/pods-replicaset-deployments.JPG)




