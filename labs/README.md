# Individual Labs
These labs are my attempt to have a sequenced way of iteratively studying for the CKA exam. This page enumerates and describes each one at a high level. Each lab has it's own document describing the walk through...

[Kubernetes.io Tasks Section](https://kubernetes.io/docs/tasks/)

What I've tried to do is follow through the Kubernetes.io 'tasks' list and either consolidated or expanded on the individual items. The work comes primarily from the 'Administer a Cluster' section as this is the CKA exam. 

ALSO, I have ordered the labs in what I think is an order of importance / relevance...

My goal is to have a way to really 'practice' for the exam on my Raspberry Pi cluster. It is a small cluster that I can carry with me to work and has one master and two worker nodes. 

### Kubectl
We first need a cluster and kubectl. To ensure kubectl is installed, read through the following:
[Install Kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)

Use of the kubectl proxy to experiment with the API is easy and instructional. 

### Kubectl Exec
kubectl exec is nearly the same as Docker Exec and allows you to connect to other nodes, pods, and services. 

### Cluster Management
This tasks includes node reboots, upgrades, resizing, etc. 
#### Rebooting a Node (drain)
Given pods are typically replicated on several nodes, there's no need to worry about a specific node reboot as they will be restarted by kubectl on restart. However, to be specific about it, you can use drain to gracefully terminate pods before a reboot as well as ensuring new pods are not scheduled there. 
```
    kubectl drain mynode
    kubectl uncordon mynode
```
The uncordon command reenables scheduling. 

### Extended Node Resources
You can add user-defined 'resources' to your K8s nodes with the HTTP PATCH request. This is really pretty neat and shows out extendable K8s is. 
[Extended Node Resources](https://kubernetes.io/docs/tasks/administer-cluster/extended-resource-node/)

### Services


### Configuring 'Out Of Resource' Handling
I imagine this will be on the exam too, good walk-thru. 
[Configure Out of Resource Handling](https://kubernetes.io/docs/tasks/administer-cluster/out-of-resource/)



### Configuring Multiple Schedulers
This is probably on the exam, and this provides a good walk-thru.
[A Custom Scheduler](https://kubernetes.io/docs/tasks/administer-cluster/configure-multiple-schedulers/)



### Autoscaling DNS Service
This is an example of using node parameters to auto scale resources, such as the DNS service in this example.
[DNS Autoscaling](https://kubernetes.io/docs/tasks/administer-cluster/dns-horizontal-autoscaling/)

### Reclaim Policy for PVs
[Changing the Reclaim Policy](https://kubernetes.io/docs/tasks/administer-cluster/change-pv-reclaim-policy/)

### Change Default Storage Class
[Chaning the default storage class](https://kubernetes.io/docs/tasks/administer-cluster/change-default-storage-class/)

