# kubernetes


### Kubectl Commands 


```
kubectl run nginx --image nginx:alpine --labels "app=frontend"
kubectl create deployment nginx --image nginx:alpine
kubectl scale deployment nginx --replicas 5
kubectl set image deployment nginx nginx=nginx:1.18
```