# Cisco Networking Portfolio
**John Doe** | Aspiring Network Administrator | Learning Cisco VPN and Routing  
[LinkedIn](https://linkedin.com/in/your-profile) | [Cisco Learning Network](https://learningnetwork.cisco.com/your-profile)

![Cisco](https://img.shields.io/badge/Cisco-Networking-blue) ![VPN](https://img.shields.io/badge/Skill-VPN-green) ![CCNA](https://img.shields.io/badge/CCNA-In%20Progress-orange)

TABLE OF CONTENTS

1. Introduction  
   1.1. About Me  
   1.2. Purpose of This Portfolio  
2. Cisco RV160 Projects  
   2.1. Setting Up OpenVPN for Remote Access  
   2.2. Configuring VLANs for Network Segmentation  
   2.3. Implementing QoS for Traffic Prioritization  
3. Cisco RV320 Troubleshooting  
   3.1. 502 Bad Gateway Error After Certificate Change  
   3.2. Attempting Factory Reset  
   3.3. Recovering via TFTP Firmware Flash  
4. Skills Learned  
   4.1. VPN Configuration  
   4.2. Network Segmentation  
   4.3. Troubleshooting and Recovery  
5. Next Steps  
   5.1. Pursuing CCNA Certification  
   5.2. Exploring IPsec VPN on RV160  
   5.3. Learning Cisco CLI Commands

---

## 1. Introduction

### 1.1. About Me
I’m a beginner in networking, passionate about learning Cisco technologies through hands-on projects. I’ve worked with Cisco RV320 and RV160 routers to set up VPNs, configure VLANs, and troubleshoot real-world issues. My goal is to become a network administrator and achieve CCNA certification.

### 1.2. Purpose of This Portfolio
This portfolio showcases my Cisco networking projects to demonstrate my practical skills to potential employers. It includes detailed write-ups of my RV160 setups, a troubleshooting case study with the RV320, and my learning journey.

## 2. Cisco RV160 Projects

### 2.1. Setting Up OpenVPN for Remote Access
**Objective**: Configure an OpenVPN server on the Cisco RV160 to enable secure remote access to my home network.  
**Steps**:  
- Enabled OpenVPN in the RV160 web interface (VPN > OpenVPN).  
- Generated a CA certificate and client certificate using the router’s built-in tools.  
- Exported the `.ovpn` configuration file and set up the OpenVPN client on a Windows 11 PC.  
- Tested the connection and accessed the internal network (192.168.1.0/24).  
**Challenges**: Faced a connection timeout due to a firewall rule blocking UDP port 1194. Resolved by adding a firewall rule to allow the traffic.  
**Result**: Successfully connected to the VPN and accessed my home network remotely.  
[See Configuration File](rv160-openvpn-config.ovpn) | [Screenshots](screenshots/rv160-openvpn-setup.png)

### 2.2. Configuring VLANs for Network Segmentation
**Objective**: Segment my network into “Work” and “Guest” VLANs for better security.  
**Steps**:  
- Created VLAN 10 (Work) and VLAN 20 (Guest) in the RV160 web interface (LAN > VLAN Settings).  
- Assigned ports: LAN 1-2 to VLAN 10, LAN 3-4 to VLAN 20.  
- Configured DHCP for each VLAN with separate IP ranges (192.168.10.0/24 for Work, 192.168.20.0/24 for Guest).  
**Result**: Devices on different VLANs couldn’t communicate, improving network security.  
[Screenshots](screenshots/rv160-vlan-config.png)

### 2.3. Implementing QoS for Traffic Prioritization
**Objective**: Prioritize video streaming traffic over file downloads.  
**Steps**:  
- Enabled QoS in the RV160 web interface (QoS > Bandwidth Management).  
- Set a rule to prioritize traffic on port 1935 (used for RTMP streaming) over other traffic.  
**Result**: Streaming quality improved significantly during high network usage.  
[Screenshots](screenshots/rv160-qos-config.png)

## 3. Cisco RV320 Troubleshooting

### 3.1. 502 Bad Gateway Error After Certificate Change
**Issue**: Encountered a 502 Bad Gateway error after replacing the RV320’s default certificate with a newly generated one.  
**Impact**: Lost access to the admin interface (https://192.168.1.1).  
**Details**: The router’s Nginx server (v1.16.1) couldn’t communicate with the backend service, likely due to a certificate misconfiguration.

### 3.2. Attempting Factory Reset
**Steps**:  
- Pressed and held the reset button for 30 seconds, but the router didn’t fully reset.  
- Tried the 30-30-30 method (hold reset, unplug, hold, plug back in), but still no access.  
**Finding**: The RV320 has a known issue where hardware resets don’t clear custom certificates.

### 3.3. Recovering via TFTP Firmware Flash
**Solution**: Used TFTP to flash the firmware and regain access.  
**Steps**:  
- Downloaded the latest RV320 firmware (RV32X_v1.5.1.05_20191001-code.bin) from Cisco’s website.  
- Put the router into TFTP mode by holding the reset button while powering on.  
- Used Tftpd64 to upload the firmware to 192.168.1.1.  
**Result**: Router rebooted with factory settings, and I regained access to the admin interface.  
[See TFTP Log](logs/rv320-tftp-recovery.log)

## 4. Skills Learned

### 4.1. VPN Configuration
- Set up OpenVPN on the RV160 for secure remote access.  
- Learned how to generate certificates and configure firewall rules for VPN traffic.

### 4.2. Network Segmentation
- Configured VLANs on the RV160 to separate Work and Guest traffic.  
- Understood the importance of VLANs for security and performance.

### 4.3. Troubleshooting and Recovery
- Diagnosed and resolved a 502 Bad Gateway error on the RV320.  
- Learned how to use TFTP to recover a bricked router, a valuable skill for network administration.

## 5. Next Steps

### 5.1. Pursuing CCNA Certification
- Currently studying for the CCNA to deepen my networking knowledge.  
- Using Cisco Packet Tracer to practice configurations in a virtual lab.

### 5.2. Exploring IPsec VPN on RV160
- Plan to set up an IPsec site-to-site VPN between two RV160 routers in a lab environment.

### 5.3. Learning Cisco CLI Commands
- Starting to use the RV160’s CLI via SSH to run commands like `show running-config` and `ping`.  
- Goal is to become comfortable with CLI for more advanced Cisco devices.

---

## Connect with Me
- [LinkedIn](https://linkedin.com/in/your-profile)
- [YouTube](https://youtube.com/your-channel)
- [Personal Blog](https://your-blog.com)
