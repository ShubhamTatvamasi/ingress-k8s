# traefik


Install traefik Ingress Controller:
```bash
helm upgrade -i traefik \
  oci://ghcr.io/traefik/helm/traefik \
  --version 39.0.9 \
  --create-namespace \
  --namespace traefik
```

