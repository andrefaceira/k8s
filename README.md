
# TODO
- opensearch, opensearch dashboards
    - https://opensearch.org/docs/latest/install-and-configure/install-opensearch/helm/
    - https://github.com/opensearch-project/helm-charts/blob/main/charts/opensearch/values.yaml
- metrics server, prometheus operator, grafana
- nats
    - https://github.com/nats-io/k8s/tree/main/helm/charts/nack
    - https://github.com/nats-io/nats.net
    
- install nginx via yaml
- manage DigitalOcean with terraform






# k8s

kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo

kubectl port-forward svc/argocd-server -n argocd 8080:443

https://github.com/andrefaceira/k8s

# nginx

helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx
helm repo update
helm install nginx-ingress ingress-nginx/ingress-nginx --set controller.publishService.enabled=true

kubectl get services


# opensearch


## install generating an yaml 
helm repo add opensearch https://opensearch-project.github.io/helm-charts/
helm template . > solved.yaml

## verify it works
kubectl -n opensearch exec -it opensearch-cluster-master-0 -- /bin/bash
curl -XGET https://localhost:9200 -u 'admin:admin' --insecure

## run
kubectl port-forward opensearch/opensearch-dashboards-574f4fd977-vnhdt 5601
kubectl port-forward -n opensearch opensearch-0 9200:9200

# metrics server

kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml
