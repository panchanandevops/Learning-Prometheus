# Prometheus Lab

## Aim Of The Project:


## Prerequisites

#### To install `k3d`, you can use the following command:

```bash
curl -s https://raw.githubusercontent.com/rancher/k3d/main/install.sh | bash
```
#### Create a Namespace for `Monitoring`:

```bash
kubectl create namespace monitoring
```

#### Add Helm Repository:

```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
```

#### Install `kube-prometheus-stack` Helm Chart in `monitoring` Namespace:

```bash
helm install prometheus-stack prometheus-community/kube-prometheus-stack -n monitoring
```

#### Verify Deployment, after sometime:

```bash
kubectl get pods -n monitoring
```

#### Access Prometheus Dashboard:

```bash
kubectl port-forward svc/prometheus-stack-prometheus -n monitoring 9090:9090
```
- Open your web browser and navigate to `http://localhost:9090` to access the Prometheus dashboard.

#### Access Grafana Dashboard:

```bash
kubectl port-forward svc/prometheus-stack-grafana -n monitoring 8080:80
```

- Open your web browser and navigate to `http://localhost:8080`.


#### Login with the default credentials:
Username: admin Password: (Retrieve the password using the following command):

```bash
kubectl get secret prometheus-stack-grafana -n monitoring -o jsonpath='{.data.admin-password}' | base64 --decode ; echo
```

