---
sort: 3
---
# Installation using Vagrant

The best way to learn Kubernetes is to start using it. Lets setup Kubernetes cluster in our PC real quick  using vagrant & Virtualbox.
The idea here is not to learn/understand the installation process but to get some overview & hands-on experience of the components in Kubernetes cluster.

**Pre-req:**
- Install VirtualBox
- Install Vagrant
- Gitbash(if you are using Windows)
- 8GB RAM

There are lots of Vagrant files over the internet that you can use, I forked the one from the repo by “OpsMx” https://github.com/OpsMx
You can edit the Vagrantfile if you wish to change any of the contents.

Copy files from below Git repo to any selected directory on your PC.
I have a windows machine, I use  “Git Bash” so that its easier for a Unix guy like me.

```
$ git clone https://github.com/yaswanthvarma/Kubernetes-installation.git
```
You will see that the the repo is cloned to your current directory, move it to your desired location,  you will be running the vagrant file from this location.
![vagrantkubernetes1.jpg ](https://raw.githubusercontent.com/yaswanthvarma/kubernetes/gh-pages/images/setup/vagrant/vagrantkubernetes1.jpg)


Execute  
```
vagrant up
```
![vagrantkubernetes2.jpg ](https://raw.githubusercontent.com/yaswanthvarma/kubernetes/gh-pages/images/setup/vagrant/vagrantkubernetes2.jpg)


Let the vagrant do its thing, after sometime you will see that a kubernetes cluster is running with the config given in the Vagrantfile.
You can check the status of the machines that you just created using the vagrantfile.
![vagrantkubernetes3.jpg ](https://raw.githubusercontent.com/yaswanthvarma/kubernetes/gh-pages/images/setup/vagrant/vagrantkubernetes3.jpg)


ssh to the master node
```
vagrant ssh kmaster
```
```
kubectl cluster-info
```
![vagrantkubernetes4.jpg ](https://raw.githubusercontent.com/yaswanthvarma/kubernetes/gh-pages/images/setup/vagrant/vagrantkubernetes4.jpg)





