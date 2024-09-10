
# Module 1 - Kubernetes Components
|User|Password|
|---|---|
|lab|f5Appw0rld!|

## Access Jumphost

1. Connect to Jumphost then open Webshell
<img width="1000" alt="VSwithPolicy" src="https://github.com/bsamodro/ContainerAndKubernetes/blob/25149847079af251784e5fe6808f3ef1e043335c/images/jumphost_webshell2.png">

2. From the web shell you will ssh into the leader node:
```
ssh lab@10.1.1.5
```

- Password
```
f5Appw0rld!
```

## Node

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
```
kubectl get all,crd
```
- kube-system
```
kubectl get all -n kube-system
```

## Pod
- Describe CoreDNS (replace core dns pod with pod from above command)
```
kubectl describe pod <coredns pod> -n kube-system
```
- BusyBox
```
kubectl create namespace test
```
```
kubectl run bbox --image=docker.io/busybox -n test
```
- Get Pods
```
kubectl get pod -n test
```
You may not yet see a Completed status and instead see CrashLoopBackOff (clbo) status

- Sleep BusyBox
```
kubectl delete pod bbox -n test
```
```
kubectl run bbox -n test --image=docker.io/busybox -- /bin/sh -c 'sleep 35'
```
```
watch kubectl get pod -n test
```

## Deployment

- Deployments
```
kubectl get deployments -n kube-system
```

## Service

- Services
```
kubectl get services -n kube-system
```




