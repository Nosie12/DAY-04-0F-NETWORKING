# 🖧 Cisco Packet Tracer – Basic Network Lab

## 📌 Project Overview

This project demonstrates how to build and configure a simple Local Area Network (LAN) using Cisco Packet Tracer.

### 🎯 Objectives

- Configure a router
- Configure a switch
- Connect 3 PCs
- Assign IP addresses
- Enable communication between all devices
- Test connectivity using `ping`
- Observe packet flow using Simulation Mode

This lab reinforces foundational networking concepts required for CCNA and Network+ studies.

---

## 🏗 Network Topology

### 🔹 Devices Used

- 1x Cisco ISR 4331 Router
- 1x Cisco 2960 Switch
- 3x PCs

### 🔹 Logical Topology

> Insert screenshot here  
> Example path: `/images/Logical(Cisco Packet tracer).png`

### 🔹 Physical Topology

> Insert screenshot here  
> Example path: `/images/physical.png`

---

## 🌐 IP Addressing Scheme

| Device | Interface | IP Address     | Subnet Mask     | Default Gateway |
|--------|----------|---------------|-----------------|-----------------|
| Router | G0/0/0   | 192.168.1.1   | 255.255.255.0   | N/A             |
| Switch | VLAN 1   | 192.168.1.2   | 255.255.255.0   | 192.168.1.1     |
| PC1    | NIC      | 192.168.1.10  | 255.255.255.0   | 192.168.1.1     |
| PC2    | NIC      | 192.168.1.11  | 255.255.255.0   | 192.168.1.1     |
| PC3    | NIC      | 192.168.1.12  | 255.255.255.0   | 192.168.1.1     |

---

## 🔌 Cabling Used

| Connection        | Cable Type                |
|------------------|--------------------------|
| Router ↔ Switch | Copper Straight-Through  |
| Switch ↔ PCs    | Copper Straight-Through  |

---

## ⚙️ Router Configuration

```bash
enable
configure terminal
hostname MAIN_GATEWAY

interface gigabitEthernet 0/0/0
ip address 192.168.1.1 255.255.255.0
no shutdown
exit

end
show ip interface brief

## ⚙️ Switch Configuration

```bash
enable
configure terminal
hostname OFFICE_SWITCH

interface vlan 1
ip address 192.168.1.2 255.255.255.0
no shutdown
exit
```

## 🔒 Access Port Configuration (For PCs)

```bash
interface fastEthernet 0/1
switchport mode access
switchport access vlan 1
no shutdown
exit
```

Repeat the configuration above for:
- fa0/2
- fa0/3

## 🔐 Port Security (Optional Enhancement)

```bash
switchport port-security
switchport port-security maximum 1
switchport port-security mac-address sticky
```

### What This Does

- Allows only one device per port
- Learns and saves the MAC address automatically
- Prevents unauthorized device access

## 💻 PC Configuration

Each PC was manually configured with:

- Subnet Mask: 255.255.255.0
- Default Gateway: 192.168.1.1
- Static IP addressing

## 🧪 Connectivity Testing

From PC1 Command Prompt:

```bash
ping 192.168.1.1
ping 192.168.1.11
```

### ✅ Results

- Router reachable
- PC-to-PC communication successful
- End-to-end connectivity verified

## 🎮 Simulation Mode Observation

Using Packet Tracer Simulation Mode:

- Observed ARP request and reply
- Observed ICMP Echo Request/Reply
- Tracked packet flow between devices

Packet flow example:

```
PC1 → Switch → Router → Switch → PC2
PC2 → Switch → Router → Switch → PC1
```

## 🧠 Key Concepts Practiced

- Interface configuration
- IP addressing and subnetting
- VLAN 1 management interface
- Default gateway configuration
- Access port configuration
- Port security implementation
- Basic network troubleshooting
- Understanding ARP and ICMP

## 🚀 Skills Demonstrated

- Cisco CLI proficiency
- Layer 2 and Layer 3 fundamentals
- Network documentation
- Logical and physical topology design
- Connectivity troubleshooting

## 📥 How to Recreate This Lab

1. Install Cisco Packet Tracer from NetAcad
2. Add:
   - 1 Router (ISR 4331)
   - 1 Switch (2960)
   - 3 PCs
3. Connect devices using straight-through cables
4. Apply the configurations listed above
5. Test connectivity using ping

## 📎 Files Included

- Packet Tracer .pkt file
- Logical topology screenshot
- Physical topology screenshot
- Project documentation (README.md)

## 🏆 Outcome

All devices successfully communicate within the LAN.

This lab serves as a foundation for:

- VLAN segmentation
- Inter-VLAN routing
- DHCP configuration
- Access Control Lists (ACLs)
- WAN simulation

