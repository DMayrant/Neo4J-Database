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