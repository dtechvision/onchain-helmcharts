# A Helm Chart for Farcaster Hubs in Kubernets

This Helm Chart will spin up Hubble (a Farcaster Hub).

## Installation using Helm

1) Add the Helm Chart repository

```
helm repo add bjw-s https://bjw-s.github.io/helm-charts/
```

2) Install the Helm Chart

```
helm install bjw-s app-template -f values.yaml
```

### Installation using ArgoCD

Argo CD Application manifest to deploy the Hubble Helm chart:

```yaml
apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: hubble
  namespace: argocd # assuming ArgoCD is installed in this namespace
spec:
  project: default
  source:
    repoURL: https://dtechvision.github.io/onchain-helmcharts/
    chart: hubble
    targetRevision: 0.1.0
    helm:
      values: |
        controllers:
          hubble:
            env:
              ETH_MAINNET_RPC_URL: "YOUR_ETH_RPC_URL"
              OPTIMISM_L2_RPC_URL: "YOUR_OPTIMISM_RPC_URL"
              FC_NETWORK_ID: "1"
              RPC_SUBSCRIBE_PER_IP_LIMIT: "4"
              STATSD_METRICS_SERVER: "localhost:8125"
              HUB_OPERATOR_FID: "0"
              HUB_OPT_OUT_DIAGNOSTICS: "false"
  destination:
    server: https://kubernetes.default.svc
    namespace: farcaster # namespace where you want to deploy Hubble
  syncPolicy:
    automated:
      prune: true
      selfHeal: true
    syncOptions:
      - CreateNamespace=true
```

Make sure to replace the following values:
- `YOUR_ETH_RPC_URL` with your Ethereum mainnet RPC URL
- `YOUR_OPTIMISM_RPC_URL` with your Optimism L2 RPC URL
- Adjust the namespace in `destination.namespace` if you want to deploy to a different namespace
- Update any other environment variables or configuration values as needed
