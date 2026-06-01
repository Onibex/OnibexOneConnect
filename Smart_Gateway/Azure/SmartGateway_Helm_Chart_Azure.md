# SmartGateway Helm Chart — Quick Deployment Guide (Azure)

This Helm Chart deploys SmartGateway on Kubernetes (microservices + MySQL + required configuration).


Optimized for:

1. **AKS (Azure)**

---

## Before you start (requirements)

You need:

- **Compressed folder:** `SmartGatewayHelmChart.zip`
- Kubernetes **1.19+**
- Helm **3.0+**
- Cluster access (`kubectl` configured)
- Docker Hub token (**Docker Hub Token will be provided by the Onibex Team**)
- **PersistentVolume provisioner** (MySQL and DataSyncHub)
- Cloud-specific controllers / CSI drivers (LoadBalancer + Storage)

Verify tooling:

```bash
kubectl version --client
helm version
kubectl get nodes
```

---

## 1) AKS (Azure)

Select your cluster.

Run the deployment by clicking the **Connect** button.

Next, click on **Open Cloud Shell**.

Select the option **Manage files**.

Upload the ZIP folder.

Run the following command to extract the ZIP file:

```bash
unzip SmartGatewayHelmChart.zip
cd helm-deployment   # folder where Chart.yaml exists
```

---

## 2) Install (choose your cloud)

> **Note:** The `datasynchub` namespace is created automatically.

Then, execute this command:

```bash
helm install oneconnect . \
  --namespace oneconnect \
  --create-namespace \
  --values values-azure.yaml \
  --set dockerHub.token=YOUR_TOKEN
```

> ⚠️ *Note: Don't forget to insert your token in the command.*

### Verify the deployment

First, verify that the pods are healthy. To verify this, execute the following command:

```bash
# List all pods in the oneconnect namespace
kubectl get pods -n oneconnect

# For additional details (including restart count and current status)
kubectl get pods -n oneconnect -w
```

### Verify the services and get the external IP

```bash
# View all services
kubectl get svc -n oneconnect
```

Look specifically for the **`internal-frontend`** service.

### Access the platform

Once you have the `EXTERNAL-IP`, open it in your browser.

*For example*, if the IP is `172.184.99.191`:
