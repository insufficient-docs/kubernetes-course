### Creating a pod

```
kubectl run nginx --image=nginx
```

#### Validate a yaml file

```
kubectl create -f init-containers.yaml --dry-run --validate=true
```

#### Using create command - fails if pod already exits

```
kubectl create -f init-containers.yaml
```

#### Saves the resource config into annotations sections in yaml file

```
kubectl create -f init-containers.yaml --save-config
```

#### Creates or updates the pod

```
kubectl apply -f init-containers.yaml
```

Warning: kubectl apply should be used on resource created by either kubectl create --save-config or kubectl apply

### Deleting a Pod

Delete a pod (It will be recreated)

```
kubectl delete pod init-demo
```

Delete deployment that manages a pod

```
kubectl delete deployment [deployment-name]
```

### Port mapping

```
kubectl port-forward nginx-7bb7cd8db5-gw6fs 8080:80
```

### Watch pod changes

```
kubectl get pods --watch
```

### Get details of every little change the pod went through

```
kubectl describe pod init-demo
```

#### Execute command inside the pod

```
kubectl exec init-demo -it sh
```

#### Edit the yaml file

```
kubectl edit -f init-containers.yaml
```
