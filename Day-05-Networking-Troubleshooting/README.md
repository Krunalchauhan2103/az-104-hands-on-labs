# Day 05 – Azure Networking & RDP Troubleshooting

## Objective
Understand and troubleshoot Azure networking issues related to
Remote Desktop (RDP) connectivity using Network Security Groups (NSG)
and Azure Network Watcher.

This lab focuses on identifying whether connectivity issues are caused
by networking configuration, security rules, or VM-level problems.

---

## Real-World Scenario
A Windows Virtual Machine is running in Azure, but RDP connection
attempts fail even though:
- VM is powered on
- NSG rules appear to allow RDP
- Public IP is reachable

As an Azure Administrator, the task is to isolate and identify
the exact cause of the issue.

---

## Environment Details
- Resource Group: RG-Dev
- Region: Central India
- Operating System: Windows Server
- VM Type: Azure Virtual Machine
- Network Security Group: NSG-VM
- Tool Used: Azure Network Watcher

---

## Problem Observed
- RDP connection failed with error:
  "Remote Desktop can't connect to the remote computer"
- NSG inbound rule allowing TCP 3389 was present
- VM status showed Running

---

## Troubleshooting Steps Performed

### 1. Verified Network Security Group (NSG)
- Checked inbound security rules
- Confirmed TCP port 3389 (RDP) was allowed
- Verified rule priority was higher than deny rules

### 2. Checked Effective Security Rules
- Ensured no subnet-level NSG was blocking traffic
- Confirmed NIC-level NSG was applied correctly

### 3. Used Network Watcher – IP Flow Verify
- Tool: Network Watcher → IP Flow Verify
- Tested:
  - Destination IP: VM Public IP
  - Destination Port: 3389
- Result:
  - Access Allowed
  - Security Rule: AllowRDP
  - NSG: NSG-VM

This confirmed that Azure networking was NOT blocking the traffic.

### 4. Identified Root Cause
Since networking access was allowed:
- Issue was determined to be VM-level (OS / RDP service / credentials)
- Not a network or NSG issue

---

## Key Learnings
- NSG rules alone do not guarantee RDP access
- Network Watcher IP Flow Verify is the fastest way to confirm
  whether Azure networking is blocking traffic
- If IP Flow Verify shows "Access Allowed" and RDP still fails,
  the issue is inside the VM (OS or configuration)
- Troubleshooting must follow a layered approach:
  Network → NSG → VM OS

---

## Azure Admin Takeaways
- Always validate connectivity using Network Watcher before changing NSG rules
- Avoid randomly opening ports without verification
- Separate networking issues from VM-level issues
- This approach saves time and prevents misconfiguration

---

## Screenshots
All screenshots related to:
- RDP error
- NSG inbound rules
- Network Watcher IP Flow Verify
are available in the `images` folder.
