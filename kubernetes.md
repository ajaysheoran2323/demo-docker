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



         








  
