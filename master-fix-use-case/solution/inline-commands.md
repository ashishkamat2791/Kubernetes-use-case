### Task 1: Fix kubeconfig
```
change port from 2379 to 6443 in config file
```

### Task 2: Fix api server
```
docker ps -a |grep api
```
get the logs of exited container by doing
```
docker logs <container-id> from above
```
now go to /etc/kubernetes/manifests and correct the ca certificate path

validate It using 
```
kubectl cluster-info
```

If everything works correctly you should get output like this:
```
Kubernetes master is running at https://172.42.42.100:6443
KubeDNS is running at https://172.42.42.100:6443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy

To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.
```

### Task 3 : Fix core-dns issue
core-dns is not being deployed as a static pod hence definitions wont be available 
do the following
```
kubectl edit deploy coredns -n kube-system
```
go to container definitions image section and replace image name with *k8s.gcr.io/coredns:1.3.1*
