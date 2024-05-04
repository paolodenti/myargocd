# My ArgoCD Helm installer

## Prequisites

* [homek8s](https://github.com/paolodenti/homek8s) installed, with external-dns, cert-manager

## ArgoCD install

Main info extacted from [here](https://www.arthurkoziel.com/setting-up-argocd-with-helm/).

```bash
helm repo add argo-cd https://argoproj.github.io/argo-helm
helm dep update charts/argo-cd/

helm install argo-cd charts/argo-cd/
```

### Get the `admin` password

```bash
kubectl get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

## Install the ingress

```
helm upgrade --install argo-ingress ./argo-ingress --values values.yaml
```

Browse [ArgoCD](https://argo.paolodenti.dev), wiht `admin`/`<the password from the secret>`


## Create the app of apps

```bash
helm template charts/root-app/ | kubectl apply -f -
```

## Delete the secrets created by the manual helm install

```bash
kubectl delete secret -l owner=helm,name=argo-cd
```