# Onchain Helm Charts

A collection of helm charts to run onchain infrastructure pleasantly in Kubernetes.

- [Farcaster](https://dtech.vision/farcaster)
  - [Farcaster Hub aka "Farcaster Node"](/charts/farcaster-hubble)
  - [Shuttle App - planned]
- [Quilibrium Helm Charts - planned]
- [RETH Helm Chart - planned]

## Usage

[Helm](https://helm.sh) must be installed to use the charts.  Please refer to
Helm's [documentation](https://helm.sh/docs) to get started.

Once Helm has been set up correctly, add the repo as follows:

  helm repo add <alias> https://dtechvision.github.io/onchain-helmcharts/

If you had already added this repo earlier, run `helm repo update` to retrieve
the latest versions of the packages.  You can then run `helm search repo
<alias>` to see the charts.

To install the <chart-name> chart:

    helm install my-<chart-name> <alias>/<chart-name>

To uninstall the chart:

    helm delete my-<chart-name>

## How to setup your own Chart Repo with Github Pages

- [Helm Chart Repo via Github Pages](https://helm.sh/docs/howto/chart_releaser_action/) which is also directly documented on [Github](https://github.com/marketplace/actions/helm-chart-releaser).
