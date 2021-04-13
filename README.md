# ingress-k8s


Install ingress-nginx:
```bash
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm repo update

helm install ingress-nginx ingress-nginx/ingress-nginx \
  --create-namespace \
  --namespace ingress-nginx
```

add nginx repo
```bash
helm repo add nginx-stable https://helm.nginx.com/stable
helm repo update
```

Install Ingress Controller with LoadBalancer:
```bash
helm install nginx-ingress nginx-stable/nginx-ingress \
  --create-namespace \
  --namespace nginx-ingress \
  --version=0.6.1
```

download helm chart
```bash
helm fetch --untar nginx-stable/nginx-ingress
```

List all versions
```bash
helm search repo nginx-stable/nginx-ingress -l
```

install nginx-ingress
```bash
helm install nginx-ingress nginx-stable/nginx-ingress \
  --version=0.6.1 \
  -n nginx-ingress \
  --set controller.service.type=NodePort \
  --set controller.service.httpPort.nodePort=30080 \
  --set controller.service.httpsPort.nodePort=30443 \
  --set controller.defaultTLS.secret=nginx-ingress/letsencrypt
```

delete deployment
```bash
kubectl delete namespace nginx-ingress
```
---

add certificate to kubernetes secret
```bash
kubectl create secret tls letsencrypt \
  --key ./shubhamtatvamasi.com.key \
  --cert ./fullchain.cer \
  -n nginx-ingress
```
