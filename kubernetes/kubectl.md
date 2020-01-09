# kubectl

### View config
```
kubectl config view
```

### Edit config
```
kubectl config unset clusters.us-west-2/my-cluster
```

### Containers in pod
```
kubectl describe pod/my-pod -n namespace
```

### Exec in container
```
kubectl exec -it my-pod --container main-app -- /bin/bash
```
