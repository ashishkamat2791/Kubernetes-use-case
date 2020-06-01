# For admin role for development namespace

### Create role
```
kubectl create role developer-role --resource=pods,svc,pvc --verb="*" --namespace=development
```

### Create role-binding
```
kubectl create rolebinding developer-role-bidning --role=developer-role --user=drogo -n development
```
### Configure user in config
```
kubectl config set-credentials drogo --client-certificate=/root/drogo.crt --client-key=/root/drogo.key
```

### Create conntext in config
```
kubectl config set-context developer --cluster=kubernetes --user=drogo --namespace=development
```

### TO use context
```
kubectl use-context developer
