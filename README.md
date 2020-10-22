# kubernetes


### Kubectl Commands 


```
kubectl run nginx --image nginx:alpine --labels "app=frontend"
kubectl create deployment nginx --image nginx:alpine
kubectl scale deployment nginx --replicas 5
kubectl set image deployment nginx nginx=nginx:1.18

## Service Cluster IP
kubectl expose pod redis --port=6379 --name redis-service

## Service Node Port
kubectl expose pod nginx --port=80 --name nginx-service --type=NodePort

```