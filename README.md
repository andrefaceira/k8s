# k8s

kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo

Koe48UZK6vLow0AN
kubectl port-forward svc/argocd-server -n argocd 8080:443

# nginx

brew install helm

helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx

helm repo update

helm install nginx-ingress ingress-nginx/ingress-nginx --set controller.publishService.enabled=true

kubectl get services