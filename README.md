??? Cybersecurity Lab Setup: VirtualBox + Kali Linux
Dipson Cybersec | Home Lab Project | Tools: VirtualBox + Kali Linux

?? Project Overview
This project covers setting up a virtual cybersecurity lab using VirtualBox and Kali Linux.
The goal is a controlled, isolated environment where security tools, scanning, and other testing activities can be practiced safely, without putting a real machine or home network at risk.
The lab runs on a private NAT Network so more machines can be added later as targets for future projects.

?? Objectives
The main objectives of this project are to:
* Install and configure VirtualBox.
* Install Kali Linux as a virtual machine.
* Create a private NAT Network for the lab.
* Configure network connectivity for Kali Linux.
* Assign a consistent static IP address to the Kali VM.
* Verify network connectivity and DNS resolution.
* Document the complete setup process.

??? Purpose of the Lab
The lab provides an isolated environment for cybersecurity learning. It supports activities such as:
* Network reconnaissance
* Port scanning
* Vulnerability assessment
* Security tool practice
?? Important: This lab is used only on systems I own or have explicit permission to test.

?? Lab Configuration
ComponentConfigurationHypervisorVirtualBoxSecurity OSKali Linux 2026.2Kali RAM2048 MBProcessors2Virtual NetworkNAT NetworkNetwork Address10.0.0.0/24Kali IP Address10.0.0.2/24Default Gateway10.0.0.1DNS Server8.8.8.8
?? Lab Setup Procedure
Step 1. Install VirtualBox
VirtualBox was installed as the hypervisor for the lab.


Step 2. Install Kali Linux
Kali Linux was installed as a virtual machine inside VirtualBox.


Step 3. Create the NAT Network
A dedicated NAT Network was created in VirtualBox under File > Preferences > Network > NAT Networks.
Configuration:
Network Name: NatNetwork
IPv4 Prefix: 10.0.0.0/24
DHCP: Enabled
IPv6: Disabled

A NAT Network was used instead of plain NAT because any VM attached to it can reach other VMs on the same network directly, while still having outbound internet access. This means future target machines can be added to the same lab.

Step 4. Attach Kali Linux to the Network
The Kali Linux VM's network adapter was configured as follows:
Adapter 1
Attached to: NAT Network
Name: NatNetwork
Adapter Type: Intel PRO/1000 MT Desktop
Promiscuous Mode: Allow All
Cable Connected: Yes


Step 5. Configure a Static IP on Kali Linux
The wired connection on Kali Linux was set to Manual addressing instead of DHCP, so the machine keeps a fixed, predictable address on the lab network.
IP Address: 10.0.0.2
Subnet Mask: 255.255.255.0 (/24)
Gateway: 10.0.0.1
DNS: 8.8.8.8

A consistent IP address makes it easier to document the lab and reference the Kali machine in future exercises.

Step 6. Create a Clean VM Snapshot
After completing the network setup, a VirtualBox snapshot was taken.
Snapshot Name: Snapshot 1
Taken: after network configuration

The snapshot is a clean baseline of the lab. If a future exercise changes or breaks the VM configuration, the machine can be restored back to this point instead of rebuilding it from scratch.

?? Lab Verification
TestCommandExpected ResultCheck IP addressip aCorrect Kali IP displayed (10.0.0.2)Test gatewayping 10.0.0.1Successful repliesTest internet connectivityping 8.8.8.8Successful repliesTest DNS resolutionnslookup google.comDomain resolvesVerify snapshotRestore snapshot and run ip aBaseline configuration restored
?? What I Learned
* NAT vs NAT Network: a NAT Network lets multiple VMs on the same virtual network reach each other directly, unlike plain NAT. This is what will let future target machines join the same lab.
* Static IP configuration: how to set and verify a fixed IPv4 address, subnet mask, gateway, and DNS on Kali Linux.
* VM networking: how VirtualBox network adapters connect machines to different network types, and how that affects whether they can see each other.
* Documentation: keeping screenshots and configuration notes alongside the setup makes it easier to rebuild or explain the lab later.
* VM snapshots: taking a clean snapshot right after the network setup gives a known-good point to roll back to before trying anything risky.

?? Security & Ethical Use
This lab is for personal learning and authorized practice only. It is not used against systems I do not own or have permission to test.

?? Author
Bolaji Osanyintola (Dipson) Cybersecurity Analyst
LinkedIn: https://www.linkedin.com/in/bolaji-osanyintola

