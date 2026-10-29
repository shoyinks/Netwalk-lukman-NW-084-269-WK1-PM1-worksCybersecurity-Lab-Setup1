# Netwalk-lukman-NW-084-269-WK1-PM1-worksCybersecurity-Lab-Setup1
WEEK 1 Cybersecurity Lab Setup Sample Guide

This repository contains the step-by-step documentation for setting up an isolated virtual cybersecurity home lab environment for offensive hacking and defensive monitoring practice.

---

## 🛠️ Lab Architecture Overview
* **Hypervisor:** Oracle VirtualBox / VMware Workstation
* **Network Mode:** Isolated NAT Network (keeps malware out of the home Wi-Fi)
* **Attacker Machine:** Kali Linux (Red Team)
* **Victim Machine:** Windows 11 Enterprise / Metasploitable (Blue Team)

<img width="959" height="539" alt="image" src="https://github.com/user-attachments/assets/2ec3bc7f-031d-4ff9-9d09-148f63e88c1a" />


## 🚀 Step-by-Step Lab Implementation procedure

🛠️ Step 1: Install Hypervisor and Core Tools

• Download VirtualBox: Grab the latest installer from the official Oracle VirtualBox website.
• Install 7-Zip and Get the file archiver to unpack compressed virtual machine (.7z) templates.


🌐 Step 2: Create a Secure Isolated NAT Network

- Navigate to Global Tools or Network Settings inside VirtualBox
- Click Create and name your new virtual layout NatNetwork
- Assign the IPv4 Network Prefix block to 10.0.0.0/24
- Turn on the built-in DHCP server checkbox so VMs get addresses automatically
- Enabled IPv6 should be Disabled.

  <img width="958" height="505" alt="image" src="https://github.com/user-attachments/assets/7551962e-7a4d-4110-a14a-2695f2fbedc7" />
  

🐉 Step 3: import the Kali Linux Attacker Machine 

- Fetch the pre-configured VirtualBox .ova file from the official Kali Linux website import to virtualbox
-  Double-click the downloaded file to load the machine specifications into your hypervisor
-  Map its network adapter and Go to Kali Settings -> Network -> set Adapter 1 to Attached to: NAT Network and pick NatNetwork
-  Verify System Resource Allocation, at least 2048 MB RAM and 2 CPU cores for smooth baseline operations must be allocated.

  <img width="1280" height="800" alt="VirtualBox_kali-linux-2026 2-virtualbox-amd64_26_10_2026_12_34_51" src="https://github.com/user-attachments/assets/68345c59-78bf-45a8-a862-0b0aa38a52ba" />
  

🐧 Step 4: Configuration of the Operating System Kali Linux Network

- The configuration of the kali Linux network was done with a consistent IPv4 to apply network fix
- IP Address: 10.0.0.2; Subnet Mask: 255.255.255.0; Gateway: 10.0.0.1; DNS: 8.8.8.8

  <img width="1915" height="1009" alt="image" src="https://github.com/user-attachments/assets/c00efdfd-7bb7-4805-8ccc-5324c32d95d3" />
  

🔎 Step 5: Verify Your Lab Connectivity testing
- Test Gateway Routing: Run ping -c 3 10.0.0.1 to confirm your machine talks to the virtual hypervisor router.
- Test External Internet: Run ping -c 3 8.8.8.8 to ensure your safe NAT translations reach outside servers.
- Test Core Toolkit Functionality: Run nmap --version to verify that your network scanner engines are initialized and ready.

  <img width="959" height="511" alt="image" src="https://github.com/user-attachments/assets/cc440778-bb03-4567-85fd-72a60927a395" />
  

💾 step 6: Maintenance & Best Practices: VM Snapshots
Before executing any exploits, vulnerability scans, or malware testing, an initial system snapshot must be taken within your hypervisor. This will acts as a clean restore point if a target machine gets broken or heavily corrupted.


## 🛠️ challenges faced & How I Fixed Them
When building this lab, things did not work perfectly right away, there are some problems encountered and how I was able fixes to solve them this need to documented for this project.

Issue 1. 🧠 hardware Virtualization Error (VT-x/AMD-V)
When attempting to boot Kali Linux, VirtualBox throws a critical error stating that VT-x/AMD-V hardware virtualization is not available.

how it was fix:
- Entering BIOS/UEFI settings (usually F2, F10, F12, or Del)
- Enabling Intel VT-x / hardware virtualization.
- the configuration was saved before rebooting the computer again
- Starting the Kali VM again, After enabling virtualization,
- The VM started successfully.

Issue 2. 🌐 Networking & Routing Complications
The "NAT" vs. "NAT Network" Mix-up

As I deploy Kali Linux and a target machine, the attacker machine can't find the target, even though both have internet access when I ran my nmap scan

how it was fix:
- I change the adapter settings on both machines to NAT Network
- And I ensure they are pointed to the exact same named network switch profile (e.g., NatNetwork)
  

## 💡 Key Lessons Learned (What I Gained From This Lab)
Building this environment provided me hands-on experience on how to create and configure virtual networks and operating systems interact for practice

The most important things I learned are:

1. **How Virtual Networks Work:
  I learned that standard "NAT" isolates machines, while a **NAT Network** acts like a real-world physical network switch. This helped me to safely connect an attacking machine to a target machine without exposing my actual home devices.
  
2. Firmware Controls Hardware:**
   I discovered that software cannot just use a computer's CPU power freely. I learned how to enter the computer's **BIOS/UEFI** menu to unlock hardware virtualization features directly at the motherboard level.
  
3. The Importance of System Baselines (Snapshots):
  I learned how to use VirtualBox **Snapshots** to save a perfect, clean state of my lab. it taught me a critical IT habit: to always create a backup point *before* running risky security tools or configuration changes.
  
4. Linux Network Troubleshooting:
   I learned how to use terminal utilities like `ip a`, `ping`, and `nmcli` to diagnose communication issues, verify system connectivity, and fix unstable network configurations.
  
5. Resource Management Balance:
   I realized that running a virtual lab requires balancing CPU and memory resources. this help to allocate just enough RAM to keep the virtual machines running without crashing the host laptop.
   

🔐 Security & Ethical Use

This laboratory is intended strictly for education purposes and practice only.


🔗 Tools & Resources

7-Zip: https://7-zip.org/download.html

VirtualBox: https://virtualbox.org/wiki/Downloads

Kali Linux: https://kali.org/get-kali


👤 Author

Lukman Ademola
Cybersecurity Professional NW-084-269

LinkedIn: www.linkedin.com/in/lukman-ademola-08127182

📌 Project Information

Program Name: Cybersecurity at Networkwalks | Week: 01 | Project: Cybersecurity & Pentesting Lab Setup | Repository: GitHub

  



 
 

