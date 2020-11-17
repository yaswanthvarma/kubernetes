---
sort: 4
---

# Namespaces

Kubernetes supports multiple virtual workspaces backed by the same physical cluster. These virtual workspaces are called namespaces.
Objects inside same namespace will be able to communicate with each other by default however it isolates objects created in it  from other namespace objects.
This is helpful when multiple teams are using the same cluster and there is a potential of name collision. 

Using the combination of an object name and a Namespace, each object gets an unique identity across the cluster.

**By default, a Kubernetes cluster is created with the following three namespaces:**
**default:** By default all the resource created in Kubernetes cluster are created in the default namespace. By default the default namespace can allow applications to run with unbounded CPU and memory requests/limits (Until someone set resource quota for the default namespace).
**kube-public:** Namespace for resources that are publicly readable by all users. This namespace is generally reserved for cluster usage.
**kube-system:** It is the Namespace for objects created by Kubernetes systems/control plane.

![namespaces ](https://raw.githubusercontent.com/yaswanthvarma/kubernetes/gh-pages/images/namespaces/namespaces1.JPG)



```
$ kubectl create –f namespace.yml                                //to create a namespace
$ kubectl get namespace                                         //list all the available namespace
$ kubectl get namespace <Namespace name>             //get a particular namespace 
$ kubectl describe namespace <Namespace name> // describe complete details about the service
$ kubectl delete namespace <Namespace name>   // delete a particular namespace
$ kubectl get pods --all-namespaces                          //list pods from all available namespace
```
