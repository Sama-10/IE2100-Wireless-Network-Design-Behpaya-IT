# IE2100 - Data Communication & Wireless Network
## Group Assignment: Network Design for Behpaya Information Technology

## 📌 Project Overview

**Module:** IE2100 - Data Communication & Wireless Network  
**Semester:** Year 2, Semester 2  
**Institution:** Sri Lanka Institute of Information Technology (SLIIT)  

**Client:** Behpaya Information Technology  
- Professional services company with approximately **50 staff**
- **2-floor head office** including:
  - Open-plan work areas
  - Meeting rooms (2)
  - Boardroom
  - Reception
  - Café/Lobby area

**Current State:** Single 300 Mbps ISP fiber link + mixed legacy devices with limited centralized management

**Objective:** Design, supply, install, configure, test, document, and support a modern wired (LAN) and wireless (WLAN) network

---

## 👥 Team Members & Roles

| Role | Name | Responsibilities |
|------|------|------------------|
| **Project Manager** | Bandara K.M.G.A.P. | Timeline management, client communication, final sign-off |
| **Network Engineer (Wired)** | Fernando C.J.S. | Switch configuration, VLAN implementation, cabling supervision |
| **Network Engineer (Wireless)** | Jayasena W.M.S.A. | AP placement, SSID design, roaming optimization, heatmap validation |
| **Security Specialist** | Dissanayake N.K. | Firewall configuration, VPN setup, RADIUS/802.1X deployment |

---

## 🎯 My Role: Wireless Network Engineer

As the Wireless Network Engineer, I was responsible for:

✅ Designing and implementing the complete wireless LAN architecture in **Cisco Packet Tracer**  
✅ Creating detailed **2-floor physical and logical topology diagrams**  
✅ Placing and configuring **4 Access Points** (Ground Floor + First Floor) with optimal coverage planning  
✅ Developing **3 SSIDs** with different security levels  
✅ Configuring **Wireless LAN Controller (WLC-2504)** for centralized management  
✅ Generating **2.4GHz and 5GHz predictive heatmaps** (≥95% coverage at -65 dBm)  
✅ Implementing **seamless roaming** for voice/video calls  
✅ Ensuring **guest isolation** with no lateral access to corporate VLANs  

---

## 📡 Wireless LAN Design

### SSID Configuration

| SSID | VLAN | Authentication | Encryption | Band | Purpose |
|------|------|----------------|------------|------|---------|
| **Behpaya_Corp** | 10 | 802.1X (RADIUS) | WPA3-Enterprise | 5/6 GHz | Staff laptops, phones |
| **Behpaya_Admin** | 20 | 802.1X + MFA | WPA3-Enterprise | 5 GHz | IT/admin devices |
| **Behpaya_Guest** | 30 | Captive Portal | WPA2-Personal | 2.4/5 GHz | Guest internet access |

### Access Point Placement

| Floor | AP ID | Location | Coverage Area |
|-------|-------|----------|---------------|
| Ground | AP-G1 | Reception | Reception area |
| Ground | AP-G2 | Open Office | Staff desks |
| Ground | AP-G3 | Meeting Room 1 | Meeting rooms |
| First | AP-F1 | Open Office | Staff desks |
| First | AP-F2 | IT Admin Office | Admin desk |
| First | AP-F3 | Boardroom | Boardroom |

### Coverage Targets

| Metric | Target |
|--------|--------|
| Minimum Signal | **-65 dBm** (5 GHz) |
| Coverage Area | **≥95%** of office space |
| Roaming Handoff | **<150 ms** |
| Channel Width | 20/40 MHz (auto) |

### RF Planning - Channel Plan (5 GHz)

| Floor | AP ID | Channel | Width | Power (dBm) |
|-------|-------|---------|-------|-------------|
| Ground | AP-G1 | 36 | 40 MHz | 17 |
| Ground | AP-G2 | 40 | 40 MHz | 20 |
| Ground | AP-G3 | 44 | 20 MHz | 14 |
| First | AP-F1 | 48 | 40 MHz | 20 |
| First | AP-F2 | 52 | 20 MHz | 14 |
| First | AP-F3 | 56 | 20 MHz | 17 |

---

## 🖧 Network Topology

### Device Inventory

| Layer | Device | Model | Quantity |
|-------|--------|-------|----------|
| Edge Layer | NGFW Firewall | FortiGate 80F | 1 |
| Core Layer | Layer 3 Switch (L3-CORE) | Cisco 3560-24PS | 1 |
| Distribution/Access Layer | Layer 2 Access Switches | Cisco 2960-24TT | 4 |
| Wireless | Access Points | Meraki MR46 (Wi-Fi 6) | 6 |

### VLAN Summary

| VLAN ID | Name | Subnet | DHCP | Gateway | Purpose |
|---------|------|--------|------|---------|---------|
| 10 | STAFF | 192.168.10.0/24 | Yes | 192.168.10.1 | Staff workstations |
| 20 | ADMIN | 192.168.20.0/28 | Yes | 192.168.20.1 | IT administration |
| 30 | GUEST | 172.16.30.0/24 | Yes | 172.16.30.1 | Guest internet only |
| 40 | NETWORK_DEV | 192.168.40.0/28 | No | 192.168.40.1 | Servers |
| 50 | VOIP | 192.168.50.0/24 | Yes | 192.168.50.1 | IP phones |
| 60 | PRINTERS | 192.168.60.0/28 | Yes | 192.168.60.1 | Network printers |
| 70 | AP_MGMT | 192.168.70.0/24 | Yes | 192.168.70.1 | AP management |
| 99 | IOT | 192.168.99.0/24 | Yes | 192.168.99.1 | IoT devices |

---

## 🔒 Security Implementation

| Threat | Mitigation |
|--------|------------|
| Unauthorized wired access | 802.1X + MAC filtering |
| Evil twin AP attack | Rogue AP detection (WIDS) |
| DoS attack on guest Wi-Fi | Rate limiting (10 Mbps/client) |
| Man-in-the-middle attack | ARP inspection + DAI |
| Data breach via guest network | L3 isolation + URL filtering |
| Weak Wi-Fi password cracking | WPA3-Enterprise + MFA |
| Physical switch port tampering | Port security + disable unused ports |

---

## 🔒 Security Implementation

| Threat | Mitigation |
|--------|------------|
| Unauthorized wired access | 802.1X + MAC filtering |
| Evil twin AP attack | Rogue AP detection (WIDS) |
| DoS attack on guest Wi-Fi | Rate limiting (10 Mbps/client) |
| Man-in-the-middle attack | ARP inspection + DAI |
| Data breach via guest network | L3 isolation + URL filtering |
| Weak Wi-Fi password cracking | WPA3-Enterprise + MFA |
| Physical switch port tampering | Port security + disable unused ports |

---

## 💰 Budget Summary (Bill of Materials)

### Hardware & Software Costs

| Item | Model | Qty | Unit Price (LKR) | Total (LKR) |
|------|-------|-----|------------------|-------------|
| NGFW Hardware | FortiGate 80F | 1 | 450,000 | 450,000 |
| NGFW Software (3-Yr) | FortiGuard Security Bundle | 1 | 270,000 | 270,000 |
| L3 Core Switch | Cisco 3560-24PS | 1 | 350,000 | 350,000 |
| Access Switch | Cisco 2960-24TT | 4 | 120,000 | 480,000 |
| Access Switch Software | Cisco ONE Foundation (24 ports) | 4 | 25,000 | 100,000 |
| Wi-Fi AP | Meraki MR46 (Wi-Fi 6) | 8 | 85,000 | 680,000 |
| Cloud Controller License (3-Yr) | Meraki Cloud MR Advanced Security | 8 | 52,000 | 416,000 |
| Cat6A Cabling | 305m box | 3 | 25,000 | 75,000 |
| Patch Panel | 24-port | 2 | 8,000 | 32,000 |
| Rack | 42U Server Rack | 1 | 60,000 | 60,000 |
| UPS | APC SMT1500 | 1 | 85,000 | 85,000 |

### Services

| Item | Cost (LKR) |
|------|-------------|
| Installation & Configuration | 300,000 |

### Total Estimated Cost

| Category | Total (LKR) |
|----------|--------------|
| Hardware Total | 2,998,000 |
| Software Total | 786,000 |
| Services Total | 300,000 |
| **Grand Total** | **4,084,000 LKR** |

> **Note:** All prices are estimates for proposal purposes. Actual quotes available upon request.

---

## 📊 Key Achievements

✅ **≥95% coverage at -65 dBm** - Met assignment coverage KPI  
✅ **Guest isolation** - VLAN 30 cannot access corporate VLANs  
✅ **Seamless roaming** - <150 ms handoff for voice/video calls  
✅ **Centralized management** - WLC-2504 manages all APs  
✅ **Enterprise security** - WPA3-Enterprise + 802.1X + RADIUS + MFA  

---

## 🛠️ Tools Used

| Tool | Purpose |
|------|---------|
| **Cisco Packet Tracer** | Network simulation and configuration |
| **UniFi Design Center** | RF heatmaps (2.4GHz & 5GHz) |
| **Draw.io / Visio** | Network diagrams |
| **GitHub** | Version control and documentation |
