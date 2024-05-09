# NGINX PROXY CHART

Прокси для внешних локальных сервисов.

```
helm upgrade externals . 
```

# basic_auth

Create a basic auth file auth. It’s important the file generated is named auth (actually - that the secret has a key data.auth), otherwise the Ingress returns a 503.

```
USER=<USERNAME_HERE>; PASSWORD=<PASSWORD_HERE>; echo "${USER}:$(openssl passwd -stdin -apr1 <<< ${PASSWORD})" >> auth
```

Create a secret:

```
kubectl -n externals create secret generic basic-auth --from-file=auth
```