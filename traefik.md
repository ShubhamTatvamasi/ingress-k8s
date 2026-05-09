# traefik


Install traefik Ingress Controller:
```bash
helm upgrade -i traefik \
  oci://ghcr.io/traefik/helm/traefik \
  --version 40.0.0 \
  --create-namespace \
  --namespace traefik \
  --set="additionalArguments={--serversTransport.insecureSkipVerify=true}" \
  --set="ports.web.http.redirections.entryPoint.to=websecure" \
  --set="ports.web.http.redirections.entryPoint.scheme=https" \
  --set="ports.web.http.redirections.entryPoint.permanent=true"
```
> Old k8s `39.0.9`
