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

## Install istio ingress gateway and service mesh

https://istio.io/latest/docs/setup/install/

## Install k8gb

kubectl create ns k8gb

argocd app create k8gb --repo https://github.com/abaguas/k8gb-v0.15-demo --path k8gb --dest-server https://kubernetes.default.svc --dest-namespace k8gb

## Install istio

Tag the subnets with kubernetes.io/role/elb=1

helm install istio-base istio/base -n istio-system --set defaultRevision=default --create-namespace

helm install istiod istio/istiod -n istio-system --wait

kubectl create namespace istio-ingress
helm install istio-ingress istio/gateway -n istio-ingress --wait

`k annotate svc istio-ingress service.beta.kubernetes.io/aws-load-balancer-scheme=internet-facing`

## Install podinfo

kubectl create ns podinfo

kubectl label ns podinfo istio-injection=enabled

kaf argocd-app

## Configure AWS route 53 role and trust

https://kubernetes-sigs.github.io/external-dns/v0.14.0/tutorials/aws/#use-eksctl-with-eksctl-created-eks-cluster
