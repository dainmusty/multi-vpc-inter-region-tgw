# AWS Transit Gateway Multi-Region Networking (Terraform)

This project demonstrates how to build a **scalable multi-VPC and multi-region network architecture on AWS** using **AWS Transit Gateway** and **Transit Gateway Inter-Region Peering**, fully provisioned with **Terraform**.

The architecture enables **centralized, secure connectivity between VPCs across regions** while simplifying network routing and management.

---

# Architecture Overview

The platform implements a **hub-and-spoke network architecture** where Transit Gateways act as centralized routing hubs connecting multiple VPCs.

Key components include:

• Multiple VPCs deployed across AWS regions  
• AWS Transit Gateway for centralized routing  
• Transit Gateway VPC attachments  
• Transit Gateway inter-region peering  
• Route table associations and propagation  
• Infrastructure provisioning using Terraform

This architecture enables workloads in different VPCs and regions to communicate securely while maintaining **network segmentation and centralized control**.

---

# Architecture Pattern

         ┌──────────────┐
         │   VPC (App)  │
         └──────┬───────┘
                │
         ┌──────▼───────┐
         │ Transit GW A │
         │  (Region A)  │
         └──────┬───────┘
                │
      Inter-Region Peering
                │
         ┌──────▼───────┐
         │ Transit GW B │
         │  (Region B)  │
         └──────┬───────┘
                │
         ┌──────▼───────┐
         │   VPC (DB)   │
         └──────────────┘

This **hub-and-spoke pattern** allows organizations to connect multiple environments without creating complex full-mesh VPC peerings.

---

# Key Capabilities

### Centralized Network Connectivity
AWS Transit Gateway provides a central routing hub for connecting multiple VPCs.

### Multi-Region Communication
Transit Gateway peering enables secure communication between environments deployed in different AWS regions.

### Scalable Network Design
New VPCs can be attached to the Transit Gateway without redesigning the entire network.

### Infrastructure as Code
All networking infrastructure is provisioned using **Terraform**, enabling reproducible deployments and version-controlled changes.

---

# Project Structure

terraform-transit-gateway-network
│
├── vpc
│ ├── vpc-a.tf
│ └── vpc-b.tf
│
├── transit-gateway
│ ├── tgw.tf
│ ├── tgw-attachments.tf
│ └── route-tables.tf
│
├── peering
│ └── tgw-peering.tf
│
├── variables.tf
├── outputs.tf
└── provider.tf


This structure separates **network infrastructure, transit gateway configuration, and peering relationships** to keep the Terraform code modular and easier to manage.

---

# Technologies Used

AWS  
Terraform  
Amazon VPC  
AWS Transit Gateway  
Transit Gateway Inter-Region Peering

---

# Lessons Learned

### 1. Transit Gateway Simplifies VPC Connectivity

Without Transit Gateway, connecting multiple VPCs requires **full-mesh VPC peering**, which becomes difficult to manage as the number of environments grows.

Transit Gateway enables a **hub-and-spoke architecture**, significantly reducing networking complexity.

---

### 2. Inter-Region Peering Requires Explicit Route Configuration

Transit Gateway peering does not automatically propagate routes.

Each region requires **manual route table configuration** to ensure proper traffic flow between VPCs.

---

### 3. Route Tables Enable Strong Network Segmentation

Transit Gateway route tables allow fine-grained control over **which VPCs can communicate with each other**, enabling stronger network isolation between environments such as dev, staging, and production.

---

### 4. Infrastructure as Code Improves Network Consistency

Managing networking resources manually can introduce configuration drift.

Using Terraform ensures:

• repeatable infrastructure deployments  
• version-controlled network changes  
• predictable and consistent environments

---

### 5. Hub-and-Spoke Networking Improves Operational Visibility

Centralizing routing through Transit Gateway enables easier integration with:

• centralized logging  
• network monitoring  
• security inspection tools

This improves operational visibility and simplifies enterprise network governance.

---

# Real-World Use Cases

This architecture is commonly used in:

• enterprise AWS landing zones  
• multi-account cloud environments  
• hybrid cloud connectivity  
• microservice platforms spanning multiple VPCs  
• multi-region application architectures

---

# Author

Odainkey Mustapha  
Cloud Solutions Architect | DevOps & Platform Engineer

LinkedIn  
https://linkedin.com/in/odainkey-mustapha
