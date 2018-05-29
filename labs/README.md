# Individual Labs
These labs are my attempt to have a sequenced way of iteratively studying for the CKA exam. This page enumerates and describes each one at a high level. Each lab has it's own document describing the walk through...

[Kubernetes.io Tasks Section](https://kubernetes.io/docs/tasks/)

What I've tried to do is follow through the Kubernetes.io 'tasks' list and either consolidated or expanded on the individual items. The work comes primarily from the 'Administer a Cluster' section as this is the CKA exam. 

ALSO, I have ordered the labs in what I think is an order of importance / relevance...

My goal is to have a way to really 'practice' for the exam on my Raspberry Pi cluster. It is a small cluster that I can carry with me to work and has one master and two worker nodes. 
### Progress
- [x] Basics
  - [x] Kubectl
- [ ] Cluster Management
- [ ] Pods and Containers
- [ ] Storage
- [ ] Security
- [ ] Networking
- [x] Namespaces
- [ ] DNS
- [ ] Quotas
- [ ] Troubleshooting
- [ ] Monitoring, Logging, and Debugging

## Kubectl
We first need a cluster and kubectl. To ensure kubectl is installed, read through the first item. Use of the kubectl proxy to experiment with the API is easy and instructional. 

- [Install Kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- [Patching API Objects In-Place](https://kubernetes.io/docs/tasks/run-application/update-api-object-kubectl-patch/)
- [Scaling a Stateful Set](https://kubernetes.io/docs/tasks/run-application/scale-stateful-set/)
- [Deleting Stateful Sets](https://kubernetes.io/docs/tasks/run-application/delete-stateful-set/)
- [Stateful Pods - Forced Deletion](https://kubernetes.io/docs/tasks/run-application/force-delete-stateful-set-pod/)
- [ReplicaSet Rolling Updates](https://kubernetes.io/docs/tasks/run-application/rolling-update-replication-controller/)
- [Horizontal Autoscaling](https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale/)
- [Autoscaling Lab](https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale-walkthrough/)
- [Pod Disruption Budgets](https://kubernetes.io/docs/tasks/run-application/configure-pdb/)
- Need lab for Kubectl EXEC

## Cluster Management
### Rebooting a Node (drain)
Given pods are typically replicated on several nodes, there's no need to worry about a specific node reboot as they will be restarted by kubectl on restart. However, to be specific about it, you can use drain to gracefully terminate pods before a reboot as well as ensuring new pods are not scheduled there. 
```
    kubectl drain mynode
    kubectl uncordon mynode
```
The uncordon command reenables scheduling. 
### [Eviction API](https://kubernetes.io/docs/tasks/administer-cluster/safely-drain-node/)
Draining nodes with the eviction API instead of the node drain command

### Reconfigure Live Kubelet
[Dynamic Kubelet Configuration](https://kubernetes.io/docs/tasks/administer-cluster/reconfigure-kubelet/)

### Extended Node Resources
You can add user-defined 'resources' to your K8s nodes with the HTTP PATCH request. This is really pretty neat and shows how extendable K8s is. This is then used in pod creation. (see pod section)
[Extended Node Resources](https://kubernetes.io/docs/tasks/administer-cluster/extended-resource-node/)

### [Static Pods](https://kubernetes.io/docs/tasks/administer-cluster/static-pod/)
Better to use Daemon sets today

## Services

## Security
### [Securing a Cluster](https://kubernetes.io/docs/tasks/administer-cluster/securing-a-cluster/)
### [Managing Sysctls](https://kubernetes.io/docs/tasks/administer-cluster/sysctl-cluster/)
Sysctls can be disabled or enabled explicitly

## Pods and Containers
### Assigning CPU and Mem Resources
Details on assigning resources at the 'Pod' object level.
- [Memory](https://kubernetes.io/docs/tasks/configure-pod-container/assign-memory-resource/)
- [CPU](https://kubernetes.io/docs/tasks/configure-pod-container/assign-cpu-resource/)
- [QOS](https://kubernetes.io/docs/tasks/configure-pod-container/quality-service-pod/)
- [Extended Resources](https://kubernetes.io/docs/tasks/configure-pod-container/extended-resource/)
- [EmtpyDir Volume](https://kubernetes.io/docs/tasks/configure-pod-container/configure-volume-storage/)
- [Persistent Volume](https://kubernetes.io/docs/tasks/configure-pod-container/configure-persistent-volume-storage/)
- [Project Volume w/Secrets](https://kubernetes.io/docs/tasks/configure-pod-container/configure-projected-volume-storage/)
- [Security Contexts](https://kubernetes.io/docs/tasks/configure-pod-container/security-context/)
- [Setting Service Account](https://kubernetes.io/docs/tasks/configure-pod-container/configure-service-account/)
- [Pulling from a Private Repo](https://kubernetes.io/docs/tasks/configure-pod-container/pull-image-private-registry/)
- [Liveliness and Readiness Probes](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-probes/)
- [Assigning to Specific Nodes](https://kubernetes.io/docs/tasks/configure-pod-container/assign-pods-nodes/)
- [Init Containers](https://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-initialization/)
- [Hook to Lifecyle Events](https://kubernetes.io/docs/tasks/configure-pod-container/attach-handler-lifecycle-event/)
- [Using ConfigMaps](https://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/)
- [Sharing Process Namespace](https://kubernetes.io/docs/tasks/configure-pod-container/share-process-namespace/)
- [Using Kompose to Covert Docker Compose Files](https://kubernetes.io/docs/tasks/configure-pod-container/translate-compose-kubernetes/)
- [Container Commands and Arguments](https://kubernetes.io/docs/tasks/inject-data-application/define-command-argument-container/)
- [Using the Downward API](https://kubernetes.io/docs/tasks/inject-data-application/environment-variable-expose-pod-information/)
- [Downward API via a Volume](https://kubernetes.io/docs/tasks/inject-data-application/downward-api-volume-expose-pod-information/)
- [Credentials using Secrets](https://kubernetes.io/docs/tasks/inject-data-application/distribute-credentials-secure/)
- [Pod Preset Injection](https://kubernetes.io/docs/tasks/inject-data-application/podpreset/)

## Deployments, Replica Sets, and Stateful Sets
- [Deployments Lab](https://kubernetes.io/docs/tasks/run-application/run-stateless-application-deployment/)
- [Single Instance Stateful (MySQL)]()https://kubernetes.io/docs/tasks/run-application/run-single-instance-stateful-application/
- [Replicated Stateful (MySQL)](https://kubernetes.io/docs/tasks/run-application/run-replicated-stateful-application/)
- []

## Namespaces / Quotas
- [Namespace Basics](https://kubernetes.io/docs/tasks/administer-cluster/namespaces-walkthrough/)
- [More namespace Basics](https://kubernetes.io/docs/tasks/administer-cluster/namespaces/)
- [Configuring Default Mem Limits](https://kubernetes.io/docs/tasks/administer-cluster/manage-resources/memory-default-namespace/)
- [Configuring Default CPU Limits](https://kubernetes.io/docs/tasks/administer-cluster/manage-resources/cpu-default-namespace/)
- [Configuring Min/Max Mem Limits](https://kubernetes.io/docs/tasks/administer-cluster/manage-resources/memory-constraint-namespace/)
- [Configuring Min/Max CPU Limits](https://kubernetes.io/docs/tasks/administer-cluster/manage-resources/cpu-constraint-namespace/)
- [Configuring Mem/CPU Quotas](https://kubernetes.io/docs/tasks/administer-cluster/manage-resources/quota-memory-cpu-namespace/)
- [Congiguring Pod-Specific Quotas](https://kubernetes.io/docs/tasks/administer-cluster/manage-resources/quota-pod-namespace/)


## Etcd
- Etcd Basics [Operating Etcd](https://kubernetes.io/docs/tasks/administer-cluster/configure-upgrade-etcd/)

## DNS
### Customizing DNS Services
Lots of options...
[Customizing DNS Nameservers](https://kubernetes.io/docs/tasks/administer-cluster/dns-custom-nameservers/)
### Debugging DNS Resolution
[Debugging DNS](https://kubernetes.io/docs/tasks/administer-cluster/dns-debugging-resolution/)
### Autoscaling DNS Service
This is an example of using node parameters to auto scale resources, such as the DNS service in this example.
[DNS Autoscaling](https://kubernetes.io/docs/tasks/administer-cluster/dns-horizontal-autoscaling/)


### Configure Quotas for API Objects
Quotas are used to restrict the number of items that can be created. It would be nice to have a list of actual resources that can be restricted (TO-DO).
```
apiVersion: v1
kind: ResourceQuota
metadata:
  name: object-quota-demo
spec:
  hard:
    persistentvolumeclaims: "1"
    services.loadbalancers: "2"
    services.nodeports: "0"
```
### Configuring 'Out Of Resource' Handling
I imagine this will be on the exam too, good walk-thru. 
[Configure Out of Resource Handling](https://kubernetes.io/docs/tasks/administer-cluster/out-of-resource/)

## Network Policy
[Declare](https://kubernetes.io/docs/tasks/administer-cluster/declare-network-policy/)

## Encryption / Secrets
[Encryption at Rest](https://kubernetes.io/docs/tasks/administer-cluster/encrypt-data/)

### [Reserve Compute Resources](https://kubernetes.io/docs/tasks/administer-cluster/reserve-compute-resources/)
This allows you to ensure system daemons have the compute resources they need. 

### Configuring Multiple Schedulers
This is probably on the exam, and this provides a good walk-thru.
[A Custom Scheduler](https://kubernetes.io/docs/tasks/administer-cluster/configure-multiple-schedulers/)

### Node CPU Management Policies
This is a good read on how cpu resources are managed. 
[Configuring Node CPU Management Policies](https://kubernetes.io/docs/tasks/administer-cluster/cpu-management-policies/)

### [Cloud-Controller-Manager](https://kubernetes.io/docs/tasks/administer-cluster/running-cloud-controller/)
This is a component that allows cloud-specific control loops. It can be maintained by the cloud providers. 

### IP Masquerade
This is used to hide a pods IP address behind that of the Node's IP address. This is necessary when a well-known IP is needed at the receiving end. 
[IP Masquerade](https://kubernetes.io/docs/tasks/administer-cluster/ip-masq-agent/)


## Storage
### PVC Protection
As of 1.9, PVCs that are active can be protected from removal. 
[PVC Protection](https://kubernetes.io/docs/tasks/administer-cluster/pvc-protection/)
### Limit Storage Consumption
[Limit ranges on PVCs](https://kubernetes.io/docs/tasks/administer-cluster/limit-storage-consumption/)

### Reclaim Policy for PVs
[Changing the Reclaim Policy](https://kubernetes.io/docs/tasks/administer-cluster/change-pv-reclaim-policy/)

### Change Default Storage Class
[Changing the default storage class](https://kubernetes.io/docs/tasks/administer-cluster/change-default-storage-class/)

## Kubeadm

### [Using KubeAdm HA Etcd Cluster](https://kubernetes.io/docs/tasks/administer-cluster/setup-ha-etcd-with-kubeadm/)
