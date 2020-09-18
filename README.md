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

install nginx-ingress
```bash
helm install nginx-ingress nginx-stable/nginx-ingress -n nginx-ingress
```
---

add certificate to kubernetes secret
```bash
kubectl create secret tls letsencrypt \
  --key ./shubhamtatvamasi.com.key \
  --cert ./fullchain.cer
```
---


