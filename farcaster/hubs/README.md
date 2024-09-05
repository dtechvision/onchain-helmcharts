# A Helm Chart for Farcaster Hubs in Kubernets

This Helm Chart will spin up Hubble (a Farcaster Hub).

## Installation

1) Add the Helm Chart repository

```
helm repo add bjw-s https://bjw-s.github.io/helm-charts/
```

2) Install the Helm Chart

```
helm install -f values.yaml yourname bjw-s/app-template
```

with name hubble in to the onchain namespace (and create if it doesn't exist)
```
helm install -f values.yaml hubble bjw-s/app-template --namespace onchain --create-namespace                                          
```