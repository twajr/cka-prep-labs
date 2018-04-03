# kube-dns notes
Kube-dns is a pod that contains three container instances: kubedns, dnsmasq, and sidecar. To have a look at the logs of each container do this:
```
kubectl logs kube-dns-xxxx -n kube-system -c kubedns
```
You specify the -c to grab the logs of a specfic container instance inside the pod.

## What is Kubernets DNS
The kube-dns pod basically watches the API server for Pods and Services that spin up. It uses SkyDNS to then serve up queries to those pods an services. It also uses DNSMasq to caching these requests. When a pods spins up, the kube-dns overrides their local /etc/resolv.conf files so that they point only to the proxy. 

## Investigation Kube-DNS Pod
```
[root@1716bb9df96b ~]# kubectl get svc kube-dns -n kube-system
NAME       TYPE        CLUSTER-IP    EXTERNAL-IP   PORT(S)         AGE
kube-dns   ClusterIP   100.64.0.10   <none>        53/UDP,53/TCP   52m
[root@1716bb9df96b ~]# kubectl exec busybox cat /etc/resolv.conf
nameserver 100.64.0.10
search default.svc.cluster.local svc.cluster.local cluster.local google.internal
options ndots:5
```
