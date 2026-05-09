# traefik


Install traefik Ingress Controller:
```bash
helm upgrade -i traefik \
  oci://ghcr.io/traefik/helm/traefik \
  --version 40.0.0 \
  --create-namespace \
  --namespace traefik
```
> Old k8s `39.0.9`
