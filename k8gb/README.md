# k8gb Umbrella Helm Chart

This is an umbrella Helm chart that installs [k8gb](https://www.k8gb.io/) as a dependency.

## Generating Kubernetes Manifests

To generate the Kubernetes manifests from this chart, run:

```sh
helm dependency update && helm template k8gb .
```

This will render the manifests using the values in `values.yaml`.

## Overriding Values

To override values for the k8gb subchart, edit the `values.yaml` file in this directory.

Example:

```yaml
k8gb:
  someValue: yourOverride
``` 
