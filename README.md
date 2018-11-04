# metallb-on-premise
Kubernetes Metal LB for On-Prem / BareMetal

# Reference From this guide [MetalLB - Load Balance on premise](https://metallb.universe.tf/tutorial/layer2/)

# Require

1. Minikube
2. Kubectl

# Step

## minikube ip = 192.168.99.100

1. Install MetalLB
```
kubectl apply -f  metallb-v0.7.3.yaml
```

2. Apply configMap
```
kubectl apply -f  config-map.yaml
```

3. Deploy nginx service
```
kubectl apply -f nginx-deployment.yaml
```

4. Verify and Test

```
kubectl get services 
```

output
======

```
$ kubectl get service
NAME         TYPE           CLUSTER-IP       EXTERNAL-IP     PORT(S)        AGE
kubernetes   ClusterIP      10.96.0.1        <none>          443/TCP        3m
nginx        LoadBalancer   10.110.123.109   192.168.99.10   80:32649/TCP   1m
```


```
curl 192.168.99.10
```

output
======
```
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
....
```
