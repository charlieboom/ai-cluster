brew install k3d

k3d cluster create --config cluster/k3d-config.yaml

install argo:

helm repo add argo https://argoproj.github.io/argo-helm
helm repo update