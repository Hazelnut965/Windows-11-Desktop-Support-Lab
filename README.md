# Windows 11 Desktop Support & Troubleshooting Lab

## Project Overview
A hands-on IT support lab focused on diagnosing and resolving Windows 11 desktop issues using VMware Fusion on an Apple Silicon Mac. The project documents troubleshooting steps, root-cause analysis, resolutions, and verification.

## Lab Environment
- Operating System: Windows 11 ARM (64-bit)
- Virtualization: VMware Fusion
- Host: Apple Silicon Mac
- Network: NAT (Share with my Mac)
- Tools: Device Manager, Command Prompt, VMware Tools, ipconfig, ping, nslookup

## Case 01: Missing Ethernet Driver and Network Connectivity Failure

### Problem
The Windows 11 virtual machine did not have a functioning Ethernet connection. Running `ipconfig` displayed no adapter configuration, and an initial DNS lookup failed.

### Troubleshooting Steps
1. Ran `ipconfig` and confirmed that no IP configuration was displayed.
2. Opened Network Connections and found that no Ethernet adapter was listed.
3. Checked VMware Fusion settings and verified that the virtual network adapter was connected and configured to use NAT.
4. Opened Device Manager and found an Ethernet Controller with a warning icon under Other devices.
5. Installed VMware Tools 13.1.0 to provide the missing virtual network driver.
6. Confirmed that Windows recognized the vmxnet3 Ethernet Adapter.
7. Tested network connectivity and DNS resolution using Command Prompt.

### Root Cause
The VMware virtual Ethernet controller did not have a working driver installed in Windows 11.

### Resolution
Installed VMware Tools 13.1.0, allowing Windows to recognize the vmxnet3 Ethernet Adapter and establish network connectivity.

### Verification
- `ipconfig` displayed an IPv4 address and default gateway.
- `ping 8.8.8.8` returned four successful replies with 0% packet loss.
- `nslookup microsoft.com.` successfully resolved the domain name.

### Screenshots
**Before: No IP configuration**
![No IP configuration](screenshots/01-ipconfig-before.png)

**Before: Network Connections was empty**
![Empty Network Connections](screenshots/02-network-connections-empty.png)

**VMware Fusion NAT configuration**
![VMware network settings](screenshots/03-vmware-network-settings.png)

**Missing Ethernet driver in Device Manager**
![Missing Ethernet driver](screenshots/04-missing-ethernet-driver.png)

**VMware Tools installation**
![VMware Tools installation](screenshots/05-vmware-tools-setup.png)

**After: VMware Ethernet adapter recognized**
![Ethernet driver fixed](screenshots/06-ethernet-driver-fixed.png)

**After: Successful network connectivity and DNS tests**
![Network connectivity tests](screenshots/07-network-tests.png)

## Skills Demonstrated
- Windows 11 desktop troubleshooting
- Network adapter and driver diagnostics
- VMware Fusion virtual networking
- TCP/IP troubleshooting
- DNS resolution testing
- Technical documentation

## Project Status
In progress. Additional Windows desktop support troubleshooting cases will be added.
