# NGINX PROXY CHART

Прокси для внешних локальных сервисов.

```bash
helm upgrade --install externals oci://ghcr.io/litded/nginx-proxy-chart  --version 0.1.1 
```

# basic_auth

Create a basic auth file auth. It’s important the file generated is named auth (actually - that the secret has a key data.auth), otherwise the Ingress returns a 503.

```bash
USER=<USERNAME_HERE>; PASSWORD=<PASSWORD_HERE>; echo "${USER}:$(openssl passwd -stdin -apr1 <<< ${PASSWORD})" >> auth
```

Create a secret:

```bash
kubectl -n externals create secret generic basic-auth --from-file=auth
```