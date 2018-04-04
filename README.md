# cka-prep-labs
Labs to help prepare for the Certified Kubernetes Administrator (CKA) Exam

## Current Kubernetes Version
Version: 1.9.1

## Kops on GCP Setup / Notes
The labs described here run with Kubernetes on GCP using the KOPS tool. Herein are notes for creation and setup, etc.

### Adding the Dashboard
Installing the dashboard after cluster creation
```
kubectl create -f https://raw.githubusercontent.com/kubernetes/kops/master/addons/kubernetes-dashboard/v1.8.1.yaml
```
### Adding the EFK Stack
Installing the EFK stack after cluster creation. This requires a PV setup prior to launch. (Need to document)
```
kubectl create -f https://raw.githubusercontent.com/kubernetes/kops/master/addons/logging-elasticsearch/v1.6.0.yaml
```

### Getting dashboard credentials
```
$kops get secrets kube --type secret -oplaintext     # bearer token needed on first UI login
$kops get secrets admin --type secret -oplaintext    # admin login password
```
