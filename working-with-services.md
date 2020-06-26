# Working with services

## Services Types

Services can be defined in different ways:

- ClusterIP
- NodePort
- LoadBalancer
- ExternalName

### ClusterIP Service

- Only Pods within the cluster can talk to services
- Pods within the cluster can talk to each other

```yml
apiVersion: v1
kind: Service
metadata:
  name: nginx
  labels:
    app: nginx
spec:
  type: ClusterIP
  selector:
    app: nginx
  ports:
    - name: http
      port: 80
      targetPort: 80
```

Name of the service `metadata.name` above gives it its own DNS service.

### NodePort Service

- Services are exposed on a static port
- Allocates ports between 30000-32767
- Allows external call into the cluter to proxy to pods through the service(NodePort)

```yml
apiVersion: v1
kind: Service
metadata:
  name: nginx
  labels:
    app: nginx
spec:
  type: NodePort
  selector:
    app: nginx
  ports:
    - name: http
      port: 80
      targetPort: 80
      nodePort: 31000
```

### LoadBalancer Service

- External caller connects to load balancer, which then talks to the service(ClusterIp/NodePort)

```yml
apiVersion: v1
kind: Service
metadata:
  name: nginx
  labels:
    app: nginx
spec:
  type: LoadBalancer
  selector:
    app: nginx
  ports:
    - name: http
      port: 80
      targetPort: 80
```

### ExternalName Service

- Allows an external service to be proxies through our service(ExternalName), which allows us to replace the external service over time without affecting our system

```yml
apiVersion: v1
kind: Service
metadata:
  name: nginx
  labels:
    app: nginx
spec:
  type: ExternalName
  externalName: api.example.com
  ports:
    - port: 80
```

## Get running services

```
kubectl get services
```
