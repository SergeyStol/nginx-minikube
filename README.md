# nginx-minikube
The minimum working application in Kubernetes.
Use Nginx-image from the official repository (https://hub.docker.com/_/nginx).
It starts Nginx on the host machine with preinstalled minikube with ability to get access by localhost:80

# Prerequisites
* Docker (https://docs.docker.com/desktop/windows/install/, https://docs.docker.com/desktop/linux/install/, https://docs.docker.com/desktop/mac/install/)
* kubectl (https://kubernetes.io/docs/tasks/tools/)
* minikube (https://minikube.sigs.k8s.io/docs/start/)

# Running
```shell
minikube start
minikube addons enable ingress
minikube tunnel
```
Other console session
```shell
kubectl apply -f nginx-deploy.yaml
kubectl apply -f nginx-service.yaml
kubectl apply -f nginx-ingress.yaml
```

# Check if it works
```shell
curl localhost:80
```
If it works, you should see:
```shell
<!DOCTYPE html>                                   
<html>                                            
<head>                                            
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>

```


# See all pods, services ang ingresses together
```shell
echo -e "\n=== PODS ===" && kubectl get pods && echo -e "\n=== SERVICES ===" && kubectl get services && echo -e "\n=== INGRESS ===" && kubectl get ingress
```


# References
* https://hub.docker.com/_/nginx
* https://kubernetes.io/docs/concepts/services-networking/ingress/#what-is-ingress
