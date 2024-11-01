# Running the helm chart

How to run the helm chart with locally run minikube:

```bash
# install minikube
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64

# start minikube
minikube start --driver=docker
minikube addons enable ingress

# install helm
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 && chmod 700 get_helm.sh && ./get_helm.sh

# install helm chart
helm install gobpms-cluster ./ --set persistence.size=512Mi --set persistence.storageClass=standard --set replicaCount=3

# tunnel minikube
minikube tunnel
```

Now you can access the web UI from your browser: http://gobpms.127.0.0.1.nip.io

```bash
# to uninstall
helm uninstall gobpms-cluster
```
