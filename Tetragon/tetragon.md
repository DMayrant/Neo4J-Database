# Tetragon Runtime Threat Detection 🚨
```bash 
helm repo add cilium https://helm.cilium.io/

kubectl create ns tetragon 

helm install my-tetragon cilium/tetragon --version 1.7.1 -n tetragon

# Verify 
kubectl get pods -n tetragon -o wide
```