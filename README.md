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

kubectl rollout history deployment deployment-name
kubectl rollout undo deployment deployment-name

kubectl create configmap webapp-config-map --from-literal APP_COLOR=darkblue
kubectl create secret generic db-secret --from-literal DB_Host=sql01  --from-literal DB_User=root  --from-literal DB_Password=password123

kubectl drain node01 --ignore-daemonsets
kubectl drain node02 --ignore-daemonsets --force #for replicaset and other stuff
kubectl cordon node01
kubectl uncordon node01


kubeadm upgrade plan
```


### Backup Restore

```
kubectl get all -A -o yaml > backup.yml
etcdctl snapshot save snapshot.db

 ETCDCTL_API=3 etcdctl --endpoints=https://[127.0.0.1]:2379 --cacert=/etc/kubernetes/pki/etcd/ca.crt --cert=/etc/kubernetes/pki/etcd/server.crt --key=/etc/kubernetes/pki/etcd/server.key snapshot save /opt/snapshot-pre-boot.db.


etcdctl snapshot restore snapshot.db
```


### Upgrade commands

```
Run the command apt update, apt install kubeadm=1.19.0-00 and then kubeadm upgrade apply v1.19.0 and then apt install kubelet=1.19.0-00 to upgrade the kubelet on the master node```


### Authentication


```
openssl genrsa -out admin.key 2048
openssl req -new -key admin.key -subj "/CN=kube-admin/O=system:masters" -out admin.csr
openssl x509 -req -in admin.csr -CA ca.crt -CAkey cakey -out admin.crt


kubectl get csr
kubectl certificate approve <csrname> 
kubectl get csr jane -o yaml
kubectl certificate deny agent-smith
cat jane.csr | base64 | tr -d '\n' > csr.yml


kube config view
kube config use-context prod-user@mitre.org

kubectl config --kubeconfig=/root/my-kube-config use-context research #you can specify the config file


kubectl get role
kubectl get rolebinding

kubectl auth can-i delete nodes

kubectl get pods --as dev-user


kubectl create secret docker-registry regcred --docker-server=<your-registry-server> --docker-username=<your-name> --docker-password=<your-pword> --docker-email=<your-email>
```