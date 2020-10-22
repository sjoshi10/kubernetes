# Scheduling

### Taints and Tolerations


There are three types of taint effects:
* NoSchedule
* PreferNoSchedule
* NoExecute

Run the following command to taint the node with proper effects:

`kubectl taint node kube-node-0 app=frontend:NoSchedule`

You then add tolerations to Pods.


When you add toleration to Pod, it doesn't not mean pod will be deployed to matching tainted node. 



### Node Selector 

Run the following command to label the node:

`kubectl label nodes kube-node-0 app=backend`
