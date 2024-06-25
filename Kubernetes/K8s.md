```bash
kubectl config view
```

### Create deployment
```bash
kubectl create deployment <deployment_name> --image=<username>/<reponame>:<tag>
```

### Get deployment
```bash
kubectl get deployment
```

### Get pod
```bash
kubectl get pods
```

### Create service to expose deployment to outer world to access application within k8s cluster
```bash
kubectl expose deployment <deployment_name> --type=LoadBalancer --port=8080
```

### Get service
```bash
kubectl get services
```

### To access application using minikube to expose the application outside k8s cluster
```bash
minikube service <service_name>
```

### Delete service
```bash
kubectl delete service <service_name>
```

### Delete deployment
```bash
kubectl delete deployment <deployment_name>
```
