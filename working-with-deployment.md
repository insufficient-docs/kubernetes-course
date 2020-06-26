# Working with Deployment

## Creating a deployment

Deployment is a wrapper on top of replicaset, which is a wrapper on top of pod, which is a wrapper on top of container.

![deployment as wrapper](deployment-as-wrapper.png)

```
kubectl create -f deployment.yaml --save-config
```

Using `--save-config` so that we could use the `kubectl apply` henceforth to update the deployment params.

### Check the updates to pods

```
kubectl get all
```

### Check the details of the deployment

```
kubectl describe deployment.apps/nginx
```

Note: The deployment id is picked from the `get all` command output.

## Showing the deployment list

```
kubectl get deployments
```

Also, get the deployment labels:

```
kubectl get deployments --show-labels
```

Get a specific deployment:

```
kubectl get deployments -l app=nginx-deployment
```

## Scaling the deployment

```
kubectl scale -f deployment.yaml --replicas=4
```

## Deleting the deployment

```
kubectl delete -f deployment.yaml
```

## Updating the deployment

This command updates the deployment using the new params in the yaml file. Also, it uses rolling update to have zero downtime during the deployment.

```
kubectl apply -f deployment.yaml
```

## Port forwarding

I dont know what the following is doing?

```
kubectl port-forward deployment.apps/nginx 8080:80
```
