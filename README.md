# My ArgoCD Helm installer

Instruction from [here](https://www.arthurkoziel.com/setting-up-argocd-with-helm/)

Once installed, install the ingress

helm upgrade --install argo-ingress ./argo-ingress --values values.yaml

Browse [ArgoCD](https://argo.paolodenti.dev)