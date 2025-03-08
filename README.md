<h1 align="center">Welcome to Descomplicando ArgoCD no K8S 👋</h1>

> Projeto com os arquivos utilizados no curso Descomplicando Gitops com ArgoCD no Kubernetes da Linuxtips

# Instalar ArgoCD no Kubernetes

## Instalar ArgoCD manifests .yml no Kubernetes

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

# Conectando um repositorio Github no ArgoCD

No Github:

- "Settings" da sua conta
- Developer Settings
- Personal access tokens / Tokens(classic) / Generate new token (Generate new token (classic) - For general use)

Dentro do ArgoCD:

Settings -> Repositories -> Connect Repo:

- Mudar de "VIA SSH" para "VIA HTTPS"
- Adicionar um nome para a conexao (opicional)
- 'Project' sera "default"
- Adicionar o link do repositorio git (Exemplo: https://github.com/usuario/nome-do-repositorio.git)
- Username: "token"
- Password: TokenGitHubClassic
- Seleciona a flag "Skip server verification"
- Clique em "Connect" na parte superior ✅

## Author

👤 **Stenio Ignacio**

- Github: [@stenioignacio](https://github.com/stenioignacio)
- LinkedIn: [@https:\/\/www.linkedin.com\/in\/stenio-ignacio-devops\/](https://linkedin.com/in/https://www.linkedin.com/in/stenio-ignacio-devops/)
