# CEMS Helm Charts

Add the repo:

```sh
helm repo add cems https://cemsbv.github.io/helm-charts/
helm repo update
```

## Test

```sh
helm template charts/api  --debug
```

## Locally

Install dependencies:

- [ChartMuseum](https://github.com/helm/chartmuseum)
- servecm plugin:
  `helm plugin install https://github.com/jdolitsky/helm-servecm`
- push plugin:
  `helm plugin install https://github.com/chartmuseum/helm-push.git`

Run server:

```sh
helm servecm --port=8879 --storage local --storage-local-rootdir /tmp/local --context-path=/charts
```

Add local repo:

```sh
helm repo add local http://127.0.0.1:8879/charts
```

Push the chart to test:

```sh
helm cm-push charts/api local
```
