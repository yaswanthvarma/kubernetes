---
sort: 1
---
# What are containers?
A **container** is an isolated process of the application running on the Host operating system, it comes as a  package containing the application code along with configuration files, libraries, and other dependencies required for the application  to run.

A **container image** is a package/template  used to create a container.

![container ](https://github.com/yaswanthvarma/kubernetes/images/gh-pages/images/container.JPG)

Containers share a single host OS & its kernel with help of **container engine**.  They cannot access the kernel directly and have to go through the container engine which accesses the kernel to get the required resources. This is the reason why the container engine can control the CPU, RAM etc that a container can use.

Remember that you can only run containers that are compatible to use the kernel of the underlying host OS, which means you cannot run a Unix based container on a windows host and vice-versa.


##difference between containers & VMs

Let us compare containers with Virtual machines to understand containers better .

![VM vs container](https://github.com/yaswanthvarma/kubernetes/images/gh-pages/images/VMvscontainer.JPG)

**Virtual machines** are a hardware virtualization technology that  allows us to run multiple full-fledged Operating Systems on top of a **hypervisor** which manages & allocates resources to these VMs. Better isolation and security cab be achieved by using virtual machines.
VMs use full-fledged Operating systems which  need more resources to be allocated and  the boot up time would be comparatively high.

What if we could package only  the application along with libraries that are needed for it to run  and  supply this package with the required kernel and  resources,  this is called **containerization**.
A container treats itself as a complete OS and runs with in its resource limits set be the container engine.


When compared to VMs, containers have below advantages:

**Portablility:** As containers already have all required components needed for it to run the application pre-packages, it should run on **any other container engine** that provides with required resources & kernel.

**Scalable:** Since containers are lean/light weight, they can be scaled very fast and easily compared to VMs.


Now that you have some understanding on what a container is, lets dive further into understanding Kubernetes.
