# Day 04 – Availability & Scaling using VM Scale Sets (VMSS)

## Objective
Design and implement a highly available and scalable compute architecture
using Azure Virtual Machine Scale Sets (VMSS) with Windows Server and IIS.

This lab focuses on real-world production concepts such as load balancing,
autoscaling, instance resiliency, and fault tolerance.

---

## Real-World Scenario
A public-facing web application requires:
- Continuous availability
- Ability to handle sudden traffic spikes
- Automatic recovery from VM failures
- Cost optimization during low traffic periods

VM Scale Sets with Azure Load Balancer are used to meet these requirements.

---

## Environment Details
- Resource Group: RG-Dev
- Region: Central India
- Operating System: Windows Server
- VM Size: Standard B2ms
- Orchestration Mode: Uniform
- Availability Zones: 1, 2, 3

---

## Architecture Overview
- Azure Load Balancer (Public)
- Virtual Machine Scale Set (Windows)
- IIS installed automatically using Custom Data
- Autoscaling based on CPU utilization
- NAT rules configured for RDP access

---

## Tasks Performed

### 1. Created Virtual Machine Scale Set
- Deployed a Windows VM Scale Set in Uniform mode
- Distributed instances across multiple Availability Zones
- Verified instance health and provisioning state

### 2. Configured Azure Load Balancer
- Created public frontend IP
- Configured backend pool with VMSS instances
- Added health probe for HTTP (port 80)
- Created load balancing rule for web traffic

### 3. Installed IIS Automatically
- Used Custom Data (PowerShell) to install IIS on all instances
- Verified IIS default page locally and via Load Balancer public IP

### 4. Configured Autoscaling
- Minimum instances: 2
- Maximum instances: 5
- Scale-out when CPU usage > 70%
- Scale-in when CPU usage < 30%

### 5. Tested Autoscaling
- Generated CPU load on an instance
- Observed automatic scale-out (new VM instance created)
- Verified scale-in after load reduced

### 6. Configured RDP Access using NAT Rules
- Created inbound NAT rules on Load Balancer
- Connected to individual VMSS instances using IP:Port
- Resolved instance-level login issues by reimaging a failed instance

---

## Validation Results
- IIS accessible via Load Balancer public IP on port 80
- Multiple VMSS instances serving traffic
- Autoscaling working as expected
- Faulty instance successfully reimaged and recovered
- Backend pool and health probes showing healthy status

---

## Key Learnings
- VM Scale Sets provide both availability and scalability
- Instances in VMSS are stateless and replaceable
- Load Balancer is mandatory for VMSS
- Autoscaling optimizes cost and performance automatically
- Availability Zones increase resiliency
- Reimaging is the correct recovery approach for failed VMSS instances

---

## Screenshots
All screenshots related to VMSS creation, load balancer configuration,
autoscaling behavior, and IIS verification are available in the `images` folder.
