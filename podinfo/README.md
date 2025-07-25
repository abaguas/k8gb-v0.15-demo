# podinfo Umbrella Helm Chart

This is an umbrella Helm chart that installs [podinfo](https://github.com/stefanprodan/podinfo) as a dependency.

## Generating Kubernetes Manifests

To generate the Kubernetes manifests from this chart, run:

```sh
helm template podinfo .
```

This will render the manifests using the values in `values.yaml`.

## Overriding Values

To override values for the podinfo subchart, edit the `values.yaml` file in this directory.

Example:

```yaml
podinfo:
  replicaCount: 2
``` 
