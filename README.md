brew install k3d

k3d cluster create --config cluster/k3d-config.yaml

install argo:

helm repo add argo https://argoproj.github.io/argo-helm

helm repo update

helm install argocd argo/argo-cd \
  --namespace argocd \
  --create-namespace

kubectl -n argocd get pods

kubectl -n argocd get secret argocd-initial-admin-secret \
  -o jsonpath="{.data.password}" | base64 -d

kubectl port-forward svc/argocd-server -n argocd 8080:443

argocd login localhost:8080 --insecure

install istio:

istioctl install -f cluster/istio-operator.yaml -y