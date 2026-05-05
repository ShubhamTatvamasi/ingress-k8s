# traefik

Add helm repo:
```bash
helm repo add traefik https://traefik.github.io/charts
```

```bash
helm upgrade -i traefik traefik/traefik \
  --version 40.0.0-rc.2 \
  --create-namespace \
  --namespace ingress-nginx \
```

