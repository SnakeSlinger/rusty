# The Rust Journey of a Person
**John Doe** | Aspiring Network Administrator | Learning Cisco VPN and Routing  
[LinkedIn](https://linkedin.com/in/your-profile) | [Cisco Learning Network](https://learningnetwork.cisco.com/your-profile)

![Cisco](https://img.shields.io/badge/Cisco-Networking-blue) ![VPN](https://img.shields.io/badge/Skill-VPN-green) ![CCNA](https://img.shields.io/badge/CCNA-In%20Progress-orange)

TABLE OF CONTENTS

1. Common Programming Concepts    
   1.1. Variables and Mutability    
   1.2. Data Types    
   1.3. Functions    
   1.4. Comments    
   1.5. Control Flow    
2. Understanding Ownership    
   2.1. What is Ownership?    
   2.2. References and Borrowing    
   2.3. The Slice Type    
3. Using Structs to Structrure Related Data    
   3.1. Defining and Instantiating Structs    
   3.2. An Example Program Using Structs    
   3.3. Method Syntax    
4. Enums and Pattern Matching    
   4.1. Defining an Enum    
   4.2. The match Control Flow Construct    
   4.3. Concise Control Flow with if let and let else    

---

## 1. Common Programming Concepts

### 1.1. Variables and Mutability
rand = "0.8.5"  <br/><br/>
use std::io;  
use rand::Rng;  
use std::cmp::Ordering;  <br/><br/>
println!("Hello, world!");  
let mut guess = String::new();  
'''rust
sd
sd sd
'''
io::stdin().read_line(&mut guess).expect("Failed to read line");  
let secret_number = rand::thread_rng().gen_range(1..=100);  

### 1.2. Data Types
This portfolio showcases my Cisco networking projects to demonstrate my practical skills to potential employers. It includes detailed write-ups of my RV160 setups, a troubleshooting case study with the RV320, and my learning journey.

### 1.3. Functions
This portfolio showcases my Cisco networking projects to demonstrate my practical skills to potential employers. It includes detailed write-ups of my RV160 setups, a troubleshooting case study with the RV320, and my learning journey.

### 1.4. Comments
This portfolio showcases my Cisco networking projects to demonstrate my practical skills to potential employers. It includes detailed write-ups of my RV160 setups, a troubleshooting case study with the RV320, and my learning journey.

### 1.5. Control Flow
This portfolio showcases my Cisco networking projects to demonstrate my practical skills to potential employers. It includes detailed write-ups of my RV160 setups, a troubleshooting case study with the RV320, and my learning journey.

## 2. Understanding Ownership

### 2.1. What is Ownership?
**Objective**: Configure an OpenVPN server on the Cisco RV160 to enable secure remote access to my home network.  
**Steps**:  
- Enabled OpenVPN in the RV160 web interface (VPN > OpenVPN).  
- Generated a CA certificate and client certificate using the router’s built-in tools.  
- Exported the `.ovpn` configuration file and set up the OpenVPN client on a Windows 11 PC.  
- Tested the connection and accessed the internal network (192.168.1.0/24).  
**Challenges**: Faced a connection timeout due to a firewall rule blocking UDP port 1194. Resolved by adding a firewall rule to allow the traffic.  
**Result**: Successfully connected to the VPN and accessed my home network remotely.  
[See Configuration File](rv160-openvpn-config.ovpn) | [Screenshots](screenshots/rv160-openvpn-setup.png)

### 2.2. References and Borrowing
**Objective**: Segment my network into “Work” and “Guest” VLANs for better security.  
**Steps**:  
- Created VLAN 10 (Work) and VLAN 20 (Guest) in the RV160 web interface (LAN > VLAN Settings).  
- Assigned ports: LAN 1-2 to VLAN 10, LAN 3-4 to VLAN 20.  
- Configured DHCP for each VLAN with separate IP ranges (192.168.10.0/24 for Work, 192.168.20.0/24 for Guest).  
**Result**: Devices on different VLANs couldn’t communicate, improving network security.  
[Screenshots](screenshots/rv160-vlan-config.png)

### 2.3. The Slice Type
**Objective**: Prioritize video streaming traffic over file downloads.  
**Steps**:  
- Enabled QoS in the RV160 web interface (QoS > Bandwidth Management).  
- Set a rule to prioritize traffic on port 1935 (used for RTMP streaming) over other traffic.  
**Result**: Streaming quality improved significantly during high network usage.  
[Screenshots](screenshots/rv160-qos-config.png)

## 3. Using Structs to Structrure Related Data

### 3.1. Defining and Instantiating Structs
**Issue**: Encountered a 502 Bad Gateway error after replacing the RV320’s default certificate with a newly generated one.  
**Impact**: Lost access to the admin interface (https://192.168.1.1).  
**Details**: The router’s Nginx server (v1.16.1) couldn’t communicate with the backend service, likely due to a certificate misconfiguration.

### 3.2. An Example Program Using Structs
**Steps**:  
- Pressed and held the reset button for 30 seconds, but the router didn’t fully reset.  
- Tried the 30-30-30 method (hold reset, unplug, hold, plug back in), but still no access.  
**Finding**: The RV320 has a known issue where hardware resets don’t clear custom certificates.

### 3.3. Method Syntax
**Solution**: Used TFTP to flash the firmware and regain access.  
**Steps**:  
- Downloaded the latest RV320 firmware (RV32X_v1.5.1.05_20191001-code.bin) from Cisco’s website.  
- Put the router into TFTP mode by holding the reset button while powering on.  
- Used Tftpd64 to upload the firmware to 192.168.1.1.  
**Result**: Router rebooted with factory settings, and I regained access to the admin interface.  
[See TFTP Log](logs/rv320-tftp-recovery.log)

## 4. Enums and Pattern Matching

### 4.1. Defining an Enum
- Set up OpenVPN on the RV160 for secure remote access.  
- Learned how to generate certificates and configure firewall rules for VPN traffic.

### 4.2. The match Control Flow Construct
- Configured VLANs on the RV160 to separate Work and Guest traffic.  
- Understood the importance of VLANs for security and performance.

### 4.3. Concise Control Flow with if let and let else
- Diagnosed and resolved a 502 Bad Gateway error on the RV320.  
- Learned how to use TFTP to recover a bricked router, a valuable skill for network administration.

---

## Connect with Me
- [LinkedIn](https://linkedin.com/in/your-profile)
- [YouTube](https://youtube.com/your-channel)
- [Personal Blog](https://your-blog.com)
