# Module 2 Kubernetes Operation
|User|Password|
|---|---|
|lab||


## Operation Pod

- Pod Creation
```
kubectl run testpod --image=nginx:1.21 -n test
```
- Verify Pod
```
kubectl get pod -n test
```
- Delete Pod
```
kubectl delete pod testpod -n test
```
- API Resources
```
kubectl api-resources
```
- Pod Dry Run
```
kubectl run testpod --image=nginx:1.21 --port 80 -n test --dry-run=client -o yaml
```
```
kubectl run testpod --image=nginx:1.21 --port 80 -n test --dry-run=client -o yaml > testpod.yaml
```
- Testpod manifest
```
kubectl apply -f testpod.yaml
```
- Edit Pod
```
kubectl edit pod testpod -n test
```

- Arrow your cursor down to the image line, press "i" then change  nginx from 1.21 to 1.25.
  
- Once this change is made use the vim write and quit command, press
ESC (escape key)
:wq

- Describe
```
kubectl describe pod testpod -n test
```

## Operation Deployment
- Deployment
```
kubectl create deployment lab-deploy --image=nginx:1.22 --replicas=3 -n test
```
