# Day 06 – Load Balancing & Private Access

This lab documents hands-on implementation of Azure Load Balancing
(Public & Internal) and Private Endpoint–based secure access,
using real-world enterprise architecture patterns.

## Objective
Design and implement secure, scalable Azure networking by:
- Separating public and private traffic
- Using Public and Internal Load Balancers
- Restricting storage access using Private Endpoint

---

## What this lab covers
- Public Load Balancer (Internet-facing traffic)
- Internal Load Balancer (Private backend traffic)
- Frontend and Backend VM architecture
- Network Security Groups (NSG) validation
- Azure Storage Private Endpoint
- Secure blob access using Azure AD and SAS

---

## Architecture Overview
- Frontend VMs handle public web traffic (HTTP/80)
- Public Load Balancer distributes internet traffic
- Backend VMs host internal services (HTTP/8080)
- Internal Load Balancer handles private communication
- Storage Account is accessed only via Private Endpoint

---

## Environment Details
- Resource Group: RG-Dev
- Region: Central India
- OS: Windows Server
- Frontend VMs: VM-FE-01, VM-FE-02
- Backend VMs: VM-BE-01, VM-BE-02
- Public Load Balancer: PLB-Web
- Internal Load Balancer: ILB-Backend
- Storage Account: stprivatedemo123
- Blob Container: private

---

## Tasks Performed

### 1. Frontend Virtual Machines
- Created two Windows Server VMs
- Installed IIS
- Verified IIS on localhost and private IP

### 2. Public Load Balancer
- Created Standard Public Load Balancer
- Configured:
  - Frontend public IP
  - Backend pool (frontend VMs)
  - Health probe (TCP 80)
  - Load balancing rule (TCP 80)
- Verified access using Load Balancer public IP

### 3. Backend Virtual Machines
- Created backend VMs without public IP
- Installed IIS listening on port 8080
- Verified service using private IP

### 4. Internal Load Balancer
- Created Standard Internal Load Balancer
- Assigned private frontend IP
- Configured:
  - Backend pool (backend VMs)
  - Health probe (TCP 8080)
  - Load balancing rule (TCP 8080)
- Verified backend access from frontend VMs

### 5. Network Security Configuration
- Frontend NSG:
  - Allowed inbound TCP 80 from Internet
- Backend NSG:
  - Allowed inbound TCP 8080 from Virtual Network
- Verified Windows Firewall rules on all VMs

### 6. Storage Account
- Created Storage Account
- Disabled public network access
- Created private blob container

### 7. Private Endpoint
- Created Private Endpoint for Blob service
- Connected to same Virtual Network
- Integrated with Private DNS Zone
- Verified private IP resolution

### 8. Private Storage Access Test
- Direct portal upload blocked
- AzCopy upload from VM succeeded
- Access via SAS token confirmed
- Public access without authorization denied

---

## Key Learnings
- Public Load Balancer enables internet-facing apps
- Internal Load Balancer secures backend services
- Health probe success does not guarantee application access
- NSG + OS firewall must both allow traffic
- Private Endpoint fully removes public exposure
- Azure AD and SAS provide secure storage access

---

## Screenshots
All screenshots related to:
- Public Load Balancer
- Internal Load Balancer
- IIS verification
- Private Endpoint configuration
- Storage access testing

are available in the `images` folder.
