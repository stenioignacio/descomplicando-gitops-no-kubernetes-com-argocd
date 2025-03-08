# Instalar ArgoCD no Kubernetes

## Instalar ArgoCD manifests no Kubernetes

```sh
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

## Criar um port-forward para o serviço do ArgoCD dentro do Kubernetes

```sh
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

## Testar se o ArgoCD está funcional

### Terminal:

```sh
curl localhost:8080
```

### No navegador:

```sh
http://localhost:8080
```

## Fazer login usando o usuario "admin" e a senha gerada no secret dentro do Kubernetes no namespace "argocd"

### Revelar primeira credencial admin para login com admin:

```sh
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```
