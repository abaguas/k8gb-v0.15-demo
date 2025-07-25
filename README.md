## Grab cluster's kubeconfig

aws eks update-kubeconfig --region eu-west-1 --name k8gb-eu-west-1 --alias k8gb-eu-west-1

## Install ArgoCD

https://argo-cd.readthedocs.io/en/stable/getting_started/

```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

```
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

## Install k8gb

kubectl create ns k8gb

