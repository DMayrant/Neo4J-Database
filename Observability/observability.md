# Prometheus/Grafana 🔭
```bash
kubectl create ns monitor 

helm repo add prometheus-community https://prometheus-community.github.io/helm-charts

helm repo update

helm install my-prometheus prometheus-community/prometheus --version 29.37.2 - monitor
```