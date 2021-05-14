# rpi-apps

GitOps repo for applications running on our Raspberry Pi Kubernetes cluster.

## Create a sealed secret

```
kubectl -n <namespace> create secret generic <secret name> --dry-run -o json \
  --from-literal=<key>=<value> \
  | kubeseal \
  --format=yaml \
  --controller-name=sealed-secrets --controller-namespace=sealed-secrets \
  --cert=cert.pem > sealed-secret.yaml
```
