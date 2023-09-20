# metriky-z-aplikace-az-do-dashboardu

## Setup Cluster Essentials

```
slu scripts kubernetes install-ingress
slu scripts kubernetes install-cert-manager
slu scripts kubernetes install-cluster-issuer
```

## Install Maildev

```
helm upgrade --install \
  maildev \
  maildev \
  --repo https://helm.sikalabs.io \
  --namespace maildev \
  --create-namespace \
  --set host=mail.k8s.sikademo.com
```

## Install Prometheus Stack

```bash
helm upgrade --install \
  prometheus-stack \
  kube-prometheus-stack \
  --repo https://prometheus-community.github.io/helm-charts \
  -n prometheus-stack \
  --create-namespace \
  -f kubernetes/prometheus_stack/general.values.yml \
  -f kubernetes/prometheus_stack/ingress.values.yml
```
