# NETWORKWALKS-MAHEK-B084-WK1-PM1-CYBERSECURITY-LAB-SETUP
Week-1 Security lab setup


# 🔐 Cybersecurity Lab Environment Setup
 
Week 1 project, Networkwalks Cybersecurity Internship (Batch [YOUR BATCH])
 
## 📌 Project Overview
 
This repository has my Week 1 project from the Cybersecurity Internship at Networkwalks.
 
The goal was to build an isolated virtual lab on my own computer, where I can practice security tools safely without touching any real system or network. I set up VirtualBox, made a NAT network, configured Kali Linux inside it, fixed two problems I ran into, and saved the working setup as a snapshot.
 
This is my first cybersecurity project and also my first time using GitHub, so I have written down each step with screenshots.
 
## 🎯 Tasks completed 
 
- Installing 7-Zip to extract the Kali Linux VM files
- Installing and setting up Oracle VirtualBox
- Creating a NAT network so the VMs can talk to each other and reach the internet without being exposed to my main network
- Enabling the network adapter on the Kali VM and attaching it to the NAT network
- Configuring the network settings in Kali Linux and getting internet working
- Taking a snapshot of the working setup
- Troubleshooting two problems and writing down the fixes

## 🛠️ Technologies and Tools
 
- Oracle VirtualBox [7.2.22]
- Kali Linux [2026.3]
- 7-Zip
- GitHub (for documentation)
## Steps I Followed
 
### 1. Installing 7-Zip
 
The Kali Linux VM files came in a compressed format, so I installed 7-Zip first and extracted them to a folder on my computer.
 

<img width="1920" height="1200" alt="S1-7-zip install" src="https://github.com/user-attachments/assets/0d634182-1e2d-4ac7-ac56-10ea741cc675" />



### 2. Installing VirtualBox
 
I installed Oracle VirtualBox so I can run Kali Linux as a virtual machine inside my normal operating system. Everything I do in the lab stays inside the VM, so my main system is not affected.
 

<img width="1920" height="1200" alt="S2-install virtualbox" src="https://github.com/user-attachments/assets/49220ca4-6bdb-43bb-bbf7-9346ecefcaff" />



### 3. Creating the NAT Network
 
I created a NAT Network in VirtualBox. With NAT, the VMs can talk to each other and use the internet, but they stay hidden from the outside network. This keeps the lab isolated, and I can add more machines to it later to practice on.
 
<img width="1920" height="1200" alt="S3-configure NAT network" src="https://github.com/user-attachments/assets/6536062d-5155-465e-b2d2-7e57020c270f" />

 
 
### 4. Configuring Kali Linux VM Network Settings
 
I started Kali Linux and checked its network settings to make sure it was connected to the NAT network.
 
<img width="1920" height="1200" alt="S4-Kali network configure" src="https://github.com/user-attachments/assets/d8a263ae-c003-4de8-a06f-93d2d3727de6" />




### 5. Configure Kali linux Wired connections

I assigned Ip address[10.0.0.2], Netmask[24], Gateway[10.0.0.1] and DNS server [10.0.0.1] in wired connection-1 in Kali linux

<img width="1920" height="1200" alt="S5-Configure wired connection" src="https://github.com/user-attachments/assets/5438531d-d058-426f-be39-35873720080d" />


 
### 6. Fixing the Wired Connection
 
After the network setup, Kali had no internet. I fixed it using the command my instructor shared (more on this in Problem 2 below).
 
<img width="1920" height="1200" alt="S6-Fix wired connection" src="https://github.com/user-attachments/assets/7dd36898-0540-4498-8e43-f1c86953925d" />



### 7. Lab verification

|✅ Test|🧾 Command|🎯 Expected Result|
|--------|--------|--------|
|🌐 Check IP address|ip address|Correct Kali IP displayed|
|📡 Test gateway|ping 10.0.0.1|Successful replies to ping|
|🔎 Test DNS resolution|nslookup networkwalks.com|Domain resolves|


<img width="1920" height="1200" alt="S7-Lab verification" src="https://github.com/user-attachments/assets/1a6f5c3d-ae96-481f-a56f-6dee65269cb1" />


 
### 8. Taking a Snapshot
 
When everything was working, I took a snapshot of the VM. A snapshot saves the exact state of the machine, so if I break something while practicing, I can restore it in a few seconds instead of building the lab again.
 
<img width="1920" height="1200" alt="S8-snapshot" src="https://github.com/user-attachments/assets/25c5078b-783e-4e01-8be5-0ec099e42649" />


 
## 🛠️ Problems I Faced and How I Fixed Them
 
### 🚨 Issue 1: Network Option Missing in VirtualBox
 
**What happened:** 
I am using the 2026 version of VirtualBox. When I opened the VM settings, I could not find the Network option, so I could not attach the adapter to my NAT network.
 
**Root Cause:** 
The settings window was hiding some options by default.
 
**🔧 Fix Applied:** 
I switched the settings window to Expert mode and the Network option showed up. A friend showed me where to find this setting.

 <img width="1920" height="1200" alt="S9-problem-1" src="https://github.com/user-attachments/assets/7c8ddb15-bcc7-4027-8181-dd13e4d8b4e7" />

 
**📘 Lesson Learned:** 
If a configuration option appears to be missing in VirtualBox, always check whether the settings window is running in Basic or Expert Mode.
 
### 🌐 Issue 2: Kali Linux Had No Internet Connectivity

**What happened?:** 
After setting up the NAT network, Kali Linux had no internet.
 
**Root Cause:** 
This is a known issue with this version of Kali Linux on this version of VirtualBox.
 
**🔧 Fix Applied:** 
I ran the command my instructor shared in the project video, then restarted the VM. After that the internet worked.
 
```
1. sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0
2. sudo nmcli connection down "Wired connection 1"
3. sudo nmcli connection up "Wired connection 1"
```
 
**📘 Lesson Learned:** 
When setting up a virtual lab, connectivity issues are not always caused by incorrect configurations. Sometimes they are related to compatibility issues between software versions, so checking known workarounds can save a lot of troubleshooting time.

 
## Key Takeaways
 
- An isolated lab lets me practice security tools without risking real systems or my own computer
- NAT networking lets VMs talk to each other and reach the internet while staying hidden from the outside
- Snapshots save a stable state that I can restore quickly after a mistake
- When something breaks, check the settings and known version issues first
- Writing down steps with screenshots makes a project easy to follow and repeat

## 🎓 Skills and Knowledge Gained
 
Before this project I had never built a virtual lab or used GitHub. This week I learned how virtualization works, how to set up a virtual network, and how to fix network problems in Kali Linux. The two problems I faced showed me that a missing option or a failed connection often has a simple cause, and that writing down the fix can help someone else who gets stuck at the same place.
 
## ⚠️ Disclaimer
 
This project is for educational purposes only. The lab was built on my own device, and everything was done in a controlled, isolated environment that I own.
