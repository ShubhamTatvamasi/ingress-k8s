# ingress-k8s

add nginx repo
```bash
helm repo add nginx-stable https://helm.nginx.com/stable
```

update helm repo
```bash
helm repo update
```

create namespace
```bash
kubectl create namespace nginx-ingress
```

download helm chart
```bash
helm fetch --untar nginx-stable/nginx-ingress
```

install nginx-ingress
```bash
helm install nginx-ingress nginx-stable/nginx-ingress \
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
  -n nginx-ingress \
  --key ./shubhamtatvamasi.com.key \
  --cert ./fullchain.cer
```


