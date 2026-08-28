# Smart Gateway on SAP BTP (Kyma)

This folder contains the **infrastructure deployment guides** for running the Smart Gateway on SAP BTP's Kyma runtime, routed privately through SAP Cloud Connector.

> ℹ️ Looking for how to operate the platform once it's deployed (users, SAP Links, connectors, logs)? See [Using the Smart Gateway](../Using_the_Smart_Gateway/) instead.

---

## 📚 Manuals in This Folder

### 1. [Connect kubectl to Kyma](./Connect_Kubectl_to_Kyma.md)

Prerequisite step: how to connect `kubectl` to a BTP Kyma environment using an AWS EC2 instance as the intermediary host, including installing `kubectl`, Helm, and the `kubelogin` OIDC plugin.

### 2. [BTP Kyma Deployment Guide](./SmartGateway_BTP_Kyma_Deployment.md)

The full deployment workflow: installing the Strimzi Kafka operator, deploying the Kafka stack, deploying OneConnect in Cloud Connector mode, enabling Istio sidecar injection, activating the required Kyma modules, and configuring SAP Cloud Connector service channels.

---

## 🚀 Recommended Reading Path

1. [Connect kubectl to Kyma](./Connect_Kubectl_to_Kyma.md) — required before you can run any `kubectl`/Helm command against the cluster.
2. [BTP Kyma Deployment Guide](./SmartGateway_BTP_Kyma_Deployment.md) — the full installation and Cloud Connector configuration.
3. Once deployed, continue to [Using the Smart Gateway](../Using_the_Smart_Gateway/) to configure users, SAP Links, and connectors.

---

## 🔗 External Resources

- [Endpoint Customization (SM59) manual](../../SAP_Data_Modeler/Data_Modeler_Manuals/15-Endpoint_Customization_SM59.md) — configuring the SAP RFC destination.
- [Minimum Requirements](../Minimum_Requirements.md) — Kyma T-shirt sizing reference for a Proof of Concept.
- [Using the Smart Gateway](../Using_the_Smart_Gateway/) — day-to-day operation guide, once deployed.
