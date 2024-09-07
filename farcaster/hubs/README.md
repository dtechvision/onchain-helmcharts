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

3) Make sure incoming connections are allowed for at least the gossip port

You may want other connections to be made like to the grpc or http api endpoints, though if you only
use them in cluster you can use the service and your networking setup.

For the Hub it is recommended to open the gossip port to incoming traffic from the p2p network.

## Graphana Dashboard

1) Add the Datasource "Graphite"
1) Name it `Hubble Statsd Graphite`
1) Enter URL: `http://hubble-statsd.onchain.svc.cluster.local:80`
1) Press Save and Enter, unless you wan tto configure other options
1) Now go to Dashboards and import via JSON: [The Hub Graphana Dashboard](https://github.com/farcasterxyz/hub-monorepo/blob/main/apps/hubble/grafana/grafana-dashboard.json)
1) **Remove Datasource in the JSON**
1) Save Dashboard