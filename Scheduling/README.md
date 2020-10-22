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


### Node Afinity

There are three affinity types

```
requiredDuringSchedulingIgnoredDuringExecution
preferredDuringSchedulingIgnoredDuringExecution
requiredDuringSchedulingRequiredDuringExecution
```

You can see the operator In being used in the example. The new node affinity syntax supports the following operators: `In, NotIn, Exists, DoesNotExist, Gt, Lt`. You can use NotIn and DoesNotExist to achieve node anti-affinity behavior, or use node taints to repel pods from specific nodes.