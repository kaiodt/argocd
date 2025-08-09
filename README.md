# ArgoCD

## Local Setup

### Installation with Helm

- Add repository:

  ```shell
  helm repo add argo https://argoproj.github.io/argo-helm
  ```

- Update repositories:

  ```shell
  helm repo update
  ```

- Install ArgoCD:

  ```shell
  helm upgrade argo-cd argo/argo-cd --version 8.2.5 \
  --namespace argocd --create-namespace \
  --install \
  --values argocd/values.yaml
  ```

- Get initial password:

  ```shell
  kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
  ```

- Access `https://argocd.example.com` and accept the certificate.

- Log in with the credentials:

  - Username: `admin`
  - Password: Execute the command above.

### ArgoCD Application

- Deploy ArgoCD application:

  ```shell
  kubectl apply -f argocd/app-argocd.yaml
  ```
