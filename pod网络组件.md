```
kubectl apply -f \
https://raw.githubusercontent.com/coreos/flannel/2140ac876ef134e0ed5af15c65e414cf26827915/Documentation/kube-flannel.yml
```



### 主节点上调度Pod 

kubectl taint nodes --all node-role.kubernetes.io\/master-





