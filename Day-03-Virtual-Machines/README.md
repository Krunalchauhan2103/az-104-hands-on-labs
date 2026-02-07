# Day 03 – Azure Virtual Machines (Windows)

## Objective
Perform real-world Azure Virtual Machine administration tasks using Windows Server
and understand VM lifecycle, storage, availability, and cost behavior.

## Environment
- OS: Windows Server
- Resource Group: RG-Dev
- Region: Central India
- VM Size: Standard B-series
- Portal-based configuration

---

## Tasks Performed

### 1. Created Multiple Windows Virtual Machines
- Created two Windows VMs for development use
- Verified VM status, networking, and public IP assignment

### 2. Resized Virtual Machine
- Changed VM size to evaluate performance and cost impact
- Observed that resizing may require VM deallocation

### 3. Attached and Detached Data Disks
- Attached new managed data disks to VM
- Initialized and formatted disks inside Windows (Disk Management)
- Verified new drives in File Explorer
- Detached disks without data loss

### 4. Redeployed Virtual Machine
- Used Redeploy option to move VM to a new Azure host
- Observed temporary disk data warning
- Verified VM availability after redeploy

### 5. Stopped (Deallocated) Virtual Machine
- Stopped VM until status showed `Stopped (deallocated)`
- Understood compute billing stops while storage billing continues

### 6. Configured Availability Set
- Created Availability Set with fault and update domains
- Deployed two VMs into the Availability Set
- Verified fault domain and update domain distribution

---

## Key Learnings
- VM resize can require downtime
- Temporary disks lose data during redeploy
- Data disks can be attached/detached without stopping VM
- Deallocated VMs do not incur compute cost
- Availability Sets improve resiliency but must be planned before VM creation

---

## Screenshots
All screenshots are available in the `images` folder for practical verification.
