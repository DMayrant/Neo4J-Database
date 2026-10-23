# Kubernetes Runtime Threat detection and Observability 🎯

A Neo4J Graph Database was deployed in Kubernetes using helm charts. Along with Istio to run as side-car in the nginx deployment for mTLS, Smoke Test, traffic control, and policy enforcement.  Tetragon was used for run time threat detection and Prometheus and Grafana for observability.

# Update kubeconfig ☁️
```bash
aws eks update-kubeconfig \
  --region us-east-1 \
  --name aws-eks-cluster
```

# Prometheus/Grafana 🔭
```bash
kubectl create ns monitor 

helm repo add prometheus-community https://prometheus-community.github.io/helm-charts

helm install my-prometheus prometheus-community/prometheus --version 29.37.2 - monitor
```

# Tetragon Runtime Threat Detection 🚨
```bash 
helm repo add cilium https://helm.cilium.io/

kubectl create ns tetragon 

helm install my-tetragon cilium/tetragon --version 1.7.1 -n tetragon

# Verify 
kubectl get pods -n tetragon -o wide
```

# Neo4j Graph Database helm 📉
```bash
helm repo add neo4j-helm-charts https://neo4j.github.io/helm-charts/

helm repo update

helm install my-neo4j neo4j-helm-charts/neo4j \
  --version 2026.10.0 \
  -n neo4j \
  --set neo4j.name=my-neo4j \
  --set volumes.data.mode=defaultStorageClass

kubectl port-forward -n neo4j pod/my-neo4j-0 7474:7474 7687:7687  
  ```

# Istio Service mesh 
This service provides your workloads with additional 

- Observability 🔭
- mTLS 🔐
- Traffic Control 🎛️
- Policy Enforcement and Security 
- Smoke Test 
  
# Installing Istio Service Mesh with helm ☸️

```bash
helm repo add istio https://istio-release.storage.googleapis.com/charts

helm repo update 
```
# Creating namespace and installing istio base chart and pod 📈

```bash
kubectl create namespace istio-system

# Install CRDS 
helm install istio-base istio/base -n istio-system 

# Install control plane
helm install istiod istio/istiod -n istio-system
```

# Label workloads namespace for Istio Enforcement 
```bash
kubectl label namespace nginx istio-injection=enabled --overwrite
```

# Uninstall istio service-mesh and remove ns label 
```bash
kubectl label namespace nginx istio-injection=enabled-

kubectl get ns -L istio-injection 

helm uninstall istio-base istio/base -n istio-system 

helm uninstall istiod istio/istiod -n istio-system
```

# Terraform 🏗️
```bash
terraform init
terraform fmt -recursive
terraform validate
terraform plan
terraform apply
```

