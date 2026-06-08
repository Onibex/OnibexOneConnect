# Smart Gateway SaaS. AWS Architecture Overview

Onibex hosts the Smart Gateway in its own AWS Cloud infrastructure. Two connectivity patterns are available depending on the customer's SAP environment and network topology.

---

## Option A. Private ALB

> **Best for:** Customers with on-premise SAP or SAP outside of AWS.

<img width="1564" height="864" alt="smartgateway_NT_ALL_onibex-NEW AWS-SasS" src="https://github.com/user-attachments/assets/5be3d85b-1ed4-4ae6-980a-f4d53a096465" />

### How it works

SAP ECC/S4HANA initiates an outbound **RFC Type G** connection over **HTTP/HTTPS** toward Onibex's AWS Cloud.

Inside Onibex's VPC:

- An **ENI** receives inbound traffic and forwards it to an **Application Load Balancer (private IP only)**, no internet-facing endpoint is exposed.
- **SSL/TLS** is available at the ALB layer for additional encryption in transit.
- The ALB distributes traffic across **two private subnets**, each hosting a **Smart Gateway** instance paired with a **Kafka Connect / Onibex Connector**.
- The **Onibex Premium Connectors** push data downstream to the Target Cloud via **AWS Private Link**.


### Key characteristics

| Dimension | Detail |
|---|---|
| Network path | VNet Peering → private ALB (no public internet) |
| SAP connectivity | RFC Type G + HTTP/HTTPS |
| Customer AWS infra required | None |
| Security | Private IP ALB, SSL/TLS available, NACLs + Security Groups |
| Target cloud egress | AWS Private Link |

---

## Option B. Transit Gateway

> **Best for:** Enterprise customers on SAP RISE in AWS requiring private routing.

<img width="1771" height="1134" alt="smartgateway_NT_ALL_onibex-AWS-SasS" src="https://github.com/user-attachments/assets/fddb385b-884d-454c-8188-0a814f8ebc3e" />


### How it works

The **Transit Gateway** is the single private backbone connecting three parties: **SAP RISE**,
the **customer's AWS account**, and **Onibex's Cloud**. All traffic stays within the AWS network, 
no public internet involved.

1. **SAP RISE** connects to the TGW and sends data to Onibex's VPC via RFC Type G / HTTP/HTTPS.
2. **Onibex** receives the data through its TGW Attachment → ENI → private ALB → Smart Gateway
   + Kafka Connect (across two AZs).
3. **Onibex** then delivers the processed data to the **customer's Target Cloud**
   (Snowflake, Databricks, SAP HANA, ClickHouse) through Private Link.

The customer's VPC also attaches to the TGW, enabling corporate users to connect, 
optionally via a **VPN Site-to-Site** tunnel, and giving the customer's own applications
access to the same private routing fabric.

### Key characteristics

| Dimension | Detail |
|---|---|
| Network path | AWS backbone only — no public internet |
| SAP connectivity | RFC Type G + HTTP/HTTPS via TGW + VNet Peering |
| Customer AWS infra required | TGW attachment + route tables in customer VPC |
| On-premise / non-AWS SAP | Supported via VPN S2S or AWS Direct Connect |
| Security | No public IPs anywhere, NACLs + Security Groups |
| Target cloud egress | AWS Private Link |

---
