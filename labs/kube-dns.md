# kube-dns notes
Kube-dns is a pod that contains three container instances: kubedns, dnsmasq, and sidecar. To have a look at the logs of each container do this:
```
kubectl logs kube-dns-xxxx -n kube-system -c kubedns
```
You specify the -c to grab the logs of a specfic container instance inside the pod.
