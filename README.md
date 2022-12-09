# Spring Cloud Gateway

Kubernetes configs for use with [FluxCD](https://fluxcd.io) to deploy [dashaun/dev.dashaun.service.gateway](https://github.com/dashaun/dev.dashaun.service.gateway)

## Add the GitRepository

```bash
flux create source git spring-cloud-gateway \
  --url=https://github.com/dashaun-cloud/spring-cloud-gateway \
  --branch=main \
  --interval=30s \
  --export > ./clusters/cluster00/spring-cloud-gateway-source.yaml
```

## Add the Kustomization

```bash
flux create kustomization spring-cloud-gateway \
  --target-namespace=default \
  --source=spring-cloud-gateway \
  --path="./kustomize" \
  --prune=true \
  --interval=5m \
  --export > ./clusters/cluster00/spring-cloud-gateway-kustomization.yaml
```