
# Module 1 - Kubernetes Components
|User|Password|
|---|---|
|lab||


## Node

1. Connect to Jumphost then open Webshell


2. From the web shell you will ssh into the leader node:
```
ssh lab@10.1.1.5
```

- Password
```
f5Appw0rld!
```
- Get node info
```
kubectl get nodes
```
- Get node info wide
```
kubectl get nodes -o wide
```
- Node describe¶
```
kubectl describe node k3s-leader.lab
```

## Custom Resource

- get CRD info
```
kubectl get crd
```

- Describe CRD¶
```
kubectl describe crd virtualservers.k8s.nginx.org
```

## Namespaces

- View All Namespaces
```
kubectl get namespace
```

- View kube-system Namespaces
```
kubectl describe ns kube-system
```

- default






