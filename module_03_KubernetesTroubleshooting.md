# Module 3 - Kubernetes Troubleshooting
|User|Password|
|---|---|
|lab|f5Appw0rld!|

## Explain Command
kubectl explain \<resource>

- Explain Pod
```
kubectl explain pod
```
- Pod Meta
```
kubectl explain pod.metadata
```


## Get Command
kubectl get \<resource> -n \<name space>

- Get all
```
kubectl get all -n test
```

## Describe Command
kubectl describe <resource_type> <resource_name> -n <namespace>

- describe service
```
kubectl describe service -n test
```

## Events Command

- Filter Namespace
```
kubectl get events -n test
```
- Get live events
```
kubectl get events -n test --watch
```
- Filter events by namespace and resource type
```
kubectl get events -n test --field-selector involvedObject.kind=Pod
```
- Filter events by namespace, resource type, and pod name.
```
kubectl get events -n test --field-selector involvedObject.kind=Pod --field-selector involvedObject.name=testpod
```
- Sort events by time
```
kubectl get events -n test --sort-by={.lastTimestamp}
```

## Logs Command

- Pod Logs
```
kubectl logs testpod -n test
```
- Deployment logs
```
kubectl logs deploy/lab-deploy -n test
```

## Execute Command
```
kubectl exec -it testpod -n test -- /bin/bash
```

You should now see a prompt:

root@testpod:/#
```
pwd
```
```
ls -la
```
To exit the shell, type exit

But you don’t have to access the shell to run your commands, you can pass the command to the shell.

- Shell
```
kubectl exec -it testpod -n test -- ls -la
```
- Example Shell Multi-Container

kubectl exec -it <pod_name> -c <container_name> -n <namespace> -- /bin/bash


## DNS Utils
- utils
```
kubectl run dnsutils --image=registry.k8s.io/e2e-test-images/jessie-dnsutils:1.3 --restart=Always -n test -- /bin/bash -c "sleep infinity"
```
- dig
```
kubectl exec -it dnsutils -n test -- dig lab-deploy-svc.test.svc.cluster.local
```
