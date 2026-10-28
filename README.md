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
## Case 02: Windows 11 Performance and Startup Optimization

### Problem
During a Windows 11 virtual machine performance assessment, Task Manager showed high memory utilization of approximately 85%. The objective was to investigate resource usage, review startup applications, and evaluate opportunities to improve system performance.

### Troubleshooting Steps
1. Opened Task Manager and reviewed CPU, memory, disk, and GPU utilization.
2. Inspected running processes to identify resource usage.
3. Reviewed startup applications and their startup impact.
4. Identified Microsoft OneDrive as an enabled startup application with High startup impact.
5. Disabled OneDrive from startup while keeping Windows Security and VMware Tools services enabled.
6. Reviewed CPU and memory utilization again.
7. Opened File Explorer and Settings and switched between applications to verify responsiveness.

### Findings
- Initial memory utilization reached approximately 85% of the allocated 4 GB.
- OneDrive was enabled with High startup impact.
- Later memory utilization was approximately 60%, with 2.4 GB in use and 1.6 GB available.
- CPU utilization was approximately 8% during the later assessment.

### Resolution
Disabled OneDrive from automatically launching at startup to reduce unnecessary startup activity in the lab environment.

No additional RAM allocation was required during the final assessment.

### Verification
- Windows 11 opened applications and switched between them smoothly.
- Task Manager showed approximately 60% memory utilization during the final assessment.
- No significant responsiveness issues were observed during the final application test.

**Note:** The reduction in observed memory utilization cannot be attributed solely to disabling OneDrive without a controlled before-and-after comparison.

### Screenshots

**Initial performance assessment**

![Initial performance](screenshots/08-performance-initial.png)

**Running processes**

![Running processes](screenshots/09-running-processes.png)

**Startup applications before optimization**

![Startup before](screenshots/10-startup-before.png)

**Startup applications after optimization**

![Startup after](screenshots/11-startup-after.png)

**CPU performance after optimization**

![CPU performance](screenshots/12-performance-after.png)

**Final memory diagnostics**

![Memory diagnostics](screenshots/13-memory-diagnostics.png)

### Skills Demonstrated
- Windows 11 performance troubleshooting
- Task Manager resource monitoring
- CPU and memory utilization analysis
- Startup application management
- System responsiveness verification
- IT support troubleshooting documentation
