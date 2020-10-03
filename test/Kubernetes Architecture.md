---
sort: 2
---
# Kubernetes Architecture
Kubernetes cluster follows a Master-Worker kind of architecture,  the **Master-node** hosts the **control plane** components which are responsible for managing the cluster where as the **Worker-node** hosts the actual work horses for your application.

Below diagram should hep you understand the basic structure of the Kubernetes cluster.


![Kubernetes architecture ](https://github.com/yaswanthvarma/kubernetes/blob/gh-pages/images/kubernetes%20architecture.png)


**POD** : In Kubernetes, a POD can be defined as a fundamental worker unit that packages containers.  A pod can have multiple containers inside.

**kubeadm:** the command to bootstrap the cluster.
**kubectl:** the command line utility to talk to your cluster.


## Control-Plane components
### API Server
When you interact with your Kubernetes cluster using the kubectl command-line interface, you are actually communicating with the master API Server component.
The API Server is the main management point of the entire cluster. In short, it processes REST operations, validates them, and updates the corresponding objects in etcd.
The API Server is also responsible for the authentication and authorization mechanism. All API clients should be authenticated in order to interact with the API Server.



### Kube-Controller or Controller-Manager
A controller uses apiserver to watch the shared state of the cluster and makes corrective changes to the current state to change it to the desired one.
An example of such a controller is the Replication controller, which takes care of the number of pods in the system. The replication factor is configured by the user, and it's the controller’s responsibility to recreate a failed pod or remove an extra-scheduled one.Other examples of controllers are endpoints controller, namespace controller, and serviceaccounts controller.
Some examples of controllers that ship with Kubernetes include the Replication Controller, Endpoints Controller, and Namespace Controller.


### Scheduler
It is a service in master responsible for distributing the workload. It is responsible for tracking utilization of working load on cluster nodes and then placing the workload on which resources are available and accept the workload. In other words, this is the mechanism responsible for allocating pods to available nodes. The scheduler is responsible for workload utilization and allocating pod to new node.



### ETCD
Etcd is a distributed, consistent key-value store used for configuration management, service discovery, and coordinating distributed work.
When it comes to Kubernetes, etcd reliably stores the configuration data of the Kubernetes cluster, representing the state of the cluster (what nodes exist in the cluster, what pods should be running, which nodes they +are running on, and a whole lot more) at any given point of time.
As all cluster data is stored in etcd, you should always have a backup plan for it. You can easily back up your etcd data using the etcdctl snapshot save command. 
The API Server is the only Kubernetes component that connects to etcd; all the other components must go through the API Server to work with the cluster state.




## Worker-Node Components
### Kublet
Kublet is an agent that runs on each node and is responsible for watching the API Server for pods that are bound to its node and making sure those pods are running (it talks to the Docker daemon using the API over the Docker socket to manipulate containers lifecycle). It then reports back to the API Server the status of changes regarding those pods.
Kublet constantly compares the status of pods against what is declared in yaml files, and starts or deletes pods as necessary to meet the request.
The Kubelet also starts an internal HTTP server on port 10255 and exposes some endpoints (mostly for debugging, stats, and for one-off container operations such as kubectl logs or kubectl exec), such as /metrics, /metrics/cadvisor, /pods, /spec, and so on.


### Kube Proxy
This is a proxy service which runs on each node and helps in making services available to the external host. It helps in forwarding the request to correct containers and is capable of performing primitive load balancing. It makes sure that the networking environment is predictable and accessible and at the same time it is isolated as well. It manages pods on node, volumes, secrets, creating new containers’ health checkup, etc.
