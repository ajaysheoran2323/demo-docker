```

kubectl get pods                         ===> to list the pods in default namespaces 
kubectl get pods --namespace devops      ==> to list pods in devops namespace
kubectl get deployments --namespace devops     ==> to list deployments in devops namespace 
kubectl get pod <pod_name> --namespace devops  ==> to describe a particular pod 
kubectl get pod <pod_name> --namespace devops -o yaml  ==> to describe a particular pod 
kubectl describe pod <pod_name> --namespace devops   ==> describe and show latest event of pod
kubectl delete pod mypod --namespace devops   ==> to delete a pod 
```
## container in kubernetes doesnt have IP address , but pods have. containers will use pods IP addresses

```
apiVersion: v1
kind: Pod
metadata:
  name: mypod
  namespace: devops
spec:
  containers:
  - name: mycontainer-v1
    image: nginx:latest
    resources:
      requests:
         cpu: "250m"
         memory: "200Mi"
      limit:
         cpu: "500m"
         memory: "500Mi"
```

# create a `mypod.yaml` file , `mydeployment.yaml`

how to push yaml file inside kubernetes ... 

`kubectl apply -f mypod.yaml `

`kubectl apply -f mydeployment.yaml `



         
https://static.brandonpotter.com/kubernetes/DeploymentBuilder.html

Deployment
```
apiVersion: apps/v1
kind: Deployment
metadata:
  # Unique key of the Deployment instance
  name: deployment-example  
  namespace: devops
spec:
  # 3 Pods should exist at all times.
  replicas: 
  selector:
    matchLabels:
      app: deployment-example
  template:
    metadata:
      labels:
        # Apply this label to pods and default
        # the Deployment label selector to this value
        app: deployment-example
    spec:
      containers:
      - name: deployment-example
        # Run this image
        image: nginx:latest
```
===Daemonset=============================================================================
```
apiVersion: extensions/v1beta1
kind: DaemonSet
metadata:
  # Unique key of the DaemonSet instance
  name: daemonset-example
  namespace: devops
spec:
  template:
    metadata:
      labels:
        app: daemonset-example
    spec:
      containers:
      # This container is run once on each Node in the cluster
      - name: daemonset-example
        image: nginx:latest

================================================================================
```
Deployment + Service
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx
  namespace: devops
spec:
  replicas: 1
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
        - name: nginx
          image: 'nginx:latest'
          ports:
            - containerPort: 80

---
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
  namespace:
  labels:
    name: nginx-service
spec:
  ports:
    - port: 80
      targetPort: 80
      protocol: TCP
  selector:
    app: nginx
  type: LoadBalancer


```





  
