# k8s-deploy

Vagrant+Ansible+Kubernetes

scp -r vagrant@192.168.10.10:/home/vagrant/.kube $HOME/

```
kubectl get nodes
NAME         STATUS   ROLES    AGE     VERSION
k8s-master   Ready    master   6m54s   v1.16.0
k8s-node-1   Ready    <none>   2m35s   v1.16.0
```

kubectl create -f app.yaml
