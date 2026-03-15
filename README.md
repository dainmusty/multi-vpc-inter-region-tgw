# AWS Transit Gateway Multi-Region Networking (Terraform)

This project demonstrates how to build a **scalable multi-VPC and multi-region network architecture on AWS** using **AWS Transit Gateway** and **Transit Gateway Inter-Region Peering**, fully provisioned with **Terraform**.

The architecture enables secure and centralized connectivity between VPCs across regions while simplifying routing and network management.

---

# Architecture Overview

The platform implements a **hub-and-spoke network model** where Transit Gateways act as centralized routing hubs connecting multiple VPCs.

Key components include:

• Multiple VPCs deployed across different AWS regions  
• AWS Transit Gateway for centralized routing  
• Transit Gateway attachments for VPC connectivity  
• Inter-Region Transit Gateway Peering  
• Route table propagation and association  
• Infrastructure provisioning using Terraform

This architecture allows workloads in different VPCs and regions to communicate securely while maintaining clear network segmentation.

---

# Key Capabilities

### Centralized Network Connectivity
AWS Transit Gateway provides a central routing hub for connecting multiple VPCs.

### Multi-Region Communication
Transit Gateway peering enables **secure cross-region communication** between AWS environments.

### Scalable Network Design
The hub-and-spoke model simplifies adding new VPCs without complex peering relationships.

### Infrastructure as Code
All networking resources are deployed using **Terraform**, enabling reproducible and version-controlled infrastructure.

---

# Architecture Pattern

         ┌──────────────┐
         │   VPC (App)   │
         └──────┬───────┘
                │
         ┌──────▼───────┐
         │ Transit GW A │
         └──────┬───────┘
                │
      Inter-Region Peering
                │
         ┌──────▼───────┐
         │ Transit GW B │
         └──────┬───────┘
                │
         ┌──────▼───────┐
         │   VPC (DB)    │
         └──────────────┘

This pattern allows **workloads in different regions to communicate while keeping networking centralized and manageable.**

---
# AWS Transit Gateway Multi-Region Networking (Terraform)

This project demonstrates how to build a **scalable multi-VPC and multi-region network architecture on AWS** using **AWS Transit Gateway** and **Transit Gateway Inter-Region Peering**, fully provisioned with **Terraform**.

The architecture enables centralized connectivity between multiple VPCs while maintaining clear network segmentation and simplified routing management.

---

# Architecture

<p align="center">
<img src="architecture.png" width="900">
</p>

The design follows a **hub-and-spoke networking model** where Transit Gateways act as centralized routing hubs connecting VPCs across regions.

---

# Architecture Components

• Multiple Amazon VPCs across regions  
• AWS Transit Gateway (per region)  
• Transit Gateway VPC attachments  
• Transit Gateway inter-region peering  
• Route table propagation and association  
• Terraform infrastructure modules

---

# Project Structure


# Technologies Used

AWS  
Terraform  
Amazon VPC  
AWS Transit Gateway  
Transit Gateway Peering

---

# Lessons Learned

### 1. Transit Gateway Simplifies Network Architecture

Without Transit Gateway, connecting multiple VPCs requires **full-mesh VPC peering**, which becomes difficult to manage as environments grow.

Transit Gateway allows a **hub-and-spoke model**, dramatically reducing routing complexity.

---

### 2. Inter-Region Connectivity Requires Careful Route Planning

Transit Gateway peering does not automatically propagate routes.  
Each region requires **explicit route table updates** to enable cross-region communication.

---

### 3. Network Segmentation Is Easier with TGW Route Tables

Separate route tables allow you to **control which VPCs can communicate**, enabling strong network isolation between environments.

---

### 4. Infrastructure as Code Prevents Configuration Drift

Managing networking resources manually can lead to inconsistencies.

Using Terraform ensures:

• repeatable infrastructure  
• version control for network changes  
• predictable deployments

---

### 5. Centralized Networking Improves Security Visibility

By routing traffic through Transit Gateway, organizations can integrate **centralized inspection, logging, and monitoring tools** more easily.

---

# Use Cases

This architecture is commonly used for:

• multi-account AWS environments  
• hybrid cloud connectivity  
• enterprise landing zones  
• large microservice platforms  
• centralized networking across regions

---

# Author

Odainkey Mustapha  
Cloud Solutions Architect | DevOps & Platform Engineer

LinkedIn  
https://linkedin.com/in/odainkey-mustapha
