# My ArgoCD Helm installer

## Prequisites

* [homek8s](https://github.com/paolodenti/homek8s) installed, with external-dns, cert-manager

Install instruction from [here](https://www.arthurkoziel.com/setting-up-argocd-with-helm/)

Once installed, install the ingress

```
helm upgrade --install argo-ingress ./argo-ingress --values values.yaml
```

Browse [ArgoCD](https://argo.paolodenti.dev)