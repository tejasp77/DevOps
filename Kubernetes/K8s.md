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

### Create pod 
```bash
kubectl run <pod-name> --image=<image-name> -n <namespace-name>
```
For example run nginx pod from nginx image
```bash
kubectl run nginx --image=nginx -n development
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

### Get namespaces
```bash
kubectl get namespaces
```

### Get pods running in specific namespace
```bash
kubectl get pods -n <namespace_name>
```
> [!NOTE]
> If namespace is not defined, system will take default namespace.

### Create namespace
```bash
kubectl create namespace <namespace_name>
```

### Create resources
```bash
kubectl create -f <pod.yaml>
```

### Apply resources
```bash
kubectl apply -f <pod.yaml>
```
> [!NOTE]
> Create command create new k8s resource object and if resource exist in k8s the create command fails.
> Apply command create and update new or existing objects in k8s.

### Delete resources
```bash
kubectl delete -f <pod.yaml>
```

### Delete resources 
```bash
kubectl delete <object-type> <object-name>
```
For example, to delete pod
```bash
kubectl delete pod <pod-name>
```

### Get resources from all namespaces
```bash
kubectl get pods --all-namespaces
```

### Get lists of objects that k8s supports
```bash
kubectl api-resources
```

### Get count of objects that k8s supports
```bash
kubectl api-resources | wc -l
```

### Get pod information
```bash
kubectl get pods <pod-name> -o wide
```

### Get pod information in json format
```bash
kubectl get pods <pod-name> -o json
```

### Get pod information in yaml format
```bash
kubectl get pods <pod-name> -o yaml
```

### Get pod information in detail
```bash
kubectl describe pods <pod-name>
```

### Execute commands within running container from pod
```bash
kubectl exec <pod-name> -c <container-name> -- <command-type> <file>
```
For example, to get the content of nginx configuratiom from running container in nginx pod
```bash
kubectl exec <nginx-pod-name> -c nginx -- cat /etc/nginx/nginx.conf
```
