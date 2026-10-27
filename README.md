# 🌐 Enterprise Network Design & Simulation Project (Cisco Packet Tracer)

## 📌 Project Overview
Welcome! This repository documents the complete design, configuration, and implementation of an enterprise-scale multi-branch network topology built using **Cisco Packet Tracer**. 

The primary objective of this project is to connect six major regional branches (**SANA1**, **SANA2**, **TAIZ**, **ADEN**, **HODYDA**, and **MUKALLA**), configure secure device access, allocate IP addresses efficiently using Variable Length Subnet Masking (VLSM) with the base network block **41.49.0.0/16**, enable dynamic routing, and deploy centralized HTTP and DNS services.

---

## 🛠️ Step-by-Step Implementation & What Was Done

### Step 1: Topology Setup, Naming & Cabling (Task 1)
* **Device Identification:** All networking hardware—including routers, switches, and servers across all branches—has been systematically named according to the topology layout.
* **Physical Cabling:** Connected all devices using appropriate physical media (Straight-through cables for end-devices to switches, Crossover cables where applicable, and Serial links between branch routers).

### Step 2: Security & IP Subnetting (Task 2)
* **Device Security Configuration:** Hardened all routers by setting up secure administrative passwords:
  * **Console & VTY passwords:** `FCIT`
  * **Enable Secret password:** `lab`
* **VLSM Subnetting (Base IP: `41.49.0.0/16`):** Designed a complete hierarchical addressing scheme from the largest LAN to the smallest LAN and WAN links to minimize IP waste.
* **IP Allocation & DHCP:** 
  * Configured static IP addresses for router interfaces (using the first valid IP in each subnet) and servers (using the last valid IP).
  * Set up a **DHCP Server pool** on the `SANA1` router to dynamically lease IP addresses, subnet masks, gateways, and DNS settings to PCs in `LAN2`.

### Step 3: Routing, DNS, and Web Hosting (Task 3)
* **Dynamic Routing (RIPv2):** Configured Routing Information Protocol version 2 across all regional routers to allow seamless, automatic packet forwarding between all remote subnets.
* **DNS Server Configuration:** Configured the centralized DNS server to resolve the domain name `WWW.FCIT.COM` to the target IP address `210.200.100.130`.
* **HTTP Web Server Setup:** Deployed a custom HTML web page on the HTTP server featuring the exact required styling and text:
  * **Background Color:** `powderblue`
  * **Text Styling:** Red font color, italicized (`<h1>` header).
  * **Content:** 
    > *Congratulation…you complete PROJECT Successfully*
    > *[Student Name & ID]*

### Step 4: Verification & Backup (Task 4 & 5)
* **Connectivity Verification (Ping):** Verified end-to-end reachability across all subnets and tested browser resolution of `WWW.FCIT.COM` from client PCs to ensure the web page renders correctly.
* **Configuration Backup:** Saved all running router configurations directly to the centralized **TFTP server**.

---

## 📊 VLSM Subnetting Calculation Table (Base IP: 41.49.0.0/16)

| Branch / Section | Subnet Address | Subnet Mask | First IP Valid Host | Last IP Valid Host | Broadcast Address | Hosts Required |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **SANA1 (LAN2)** | `41.49.0.0` | `255.255.224.0` | `41.49.0.1` | `41.49.31.254` | `41.49.31.255` | 8,000 |
| **SANA1 (LAN1)** | `41.49.32.0` | `255.255.240.0` | `41.49.32.1` | `41.49.47.254` | `41.49.47.255` | 4,000 |
| **TAIZ (LAN1)** | `41.49.48.0` | `255.255.240.0` | `41.49.48.1` | `41.49.63.254` | `41.49.63.255` | 4,000 |
| **SANA2 (LAN2)** | `41.49.64.0` | `255.255.240.0` | `41.49.64.1` | `41.49.79.254` | `41.49.79.255` | 3,000 |
| **MUKALLA (LAN2)** | `41.49.80.0` | `255.255.240.0` | `41.49.80.1` | `41.49.95.254` | `41.49.95.255` | 2,800 |
| **TAIZ (LAN2)** | `41.49.96.0` | `255.255.248.0` | `41.49.96.1` | `41.49.103.254` | `41.49.103.255` | 2,000 |
| **SANA2 (LAN1)** | `41.49.104.0` | `255.255.248.0` | `41.49.104.1` | `41.49.111.254` | `41.49.111.255` | 1,800 |
| **ADEN (LAN1)** | `41.49.112.0` | `255.255.248.0` | `41.49.112.1` | `41.49.119.254` | `41.49.119.255` | 1,600 |
| **HODYDA (LAN1)** | `41.49.120.0` | `255.255.248.0` | `41.49.120.1` | `41.49.127.254` | `41.49.127.255` | 1,200 |
| **ADEN (LAN2)** | `41.49.128.0` | `255.255.252.0` | `41.49.128.1` | `41.49.131.254` | `41.49.131.255` | 850 |
| **HODYDA (LAN2)** | `41.49.132.0` | `255.255.255.128` | `41.49.132.1` | `41.49.132.126` | `41.49.132.127` | 120 |
| **MUKALLA (LAN1)** | `41.49.132.128` | `255.255.255.192` | `41.49.132.129` | `41.49.132.190` | `41.49.132.191` | 60 |
| **WAN1** | `41.49.132.192` | `255.255.255.252` | `41.49.132.193` | `41.49.132.194` | `41.49.132.195` | 2 |
| **WAN2** | `41.49.132.196` | `255.255.255.252` | `41.49.132.197` | `41.49.132.198` | `41.49.132.199` | 2 |
| **WAN3** | `41.49.132.200` | `255.255.255.252` | `41.49.132.201` | `41.49.132.202` | `41.49.132.203` | 2 |
| **WAN4** | `41.49.132.204` | `255.255.255.252` | `41.49.132.205` | `41.49.132.206` | `41.49.132.207` | 2 |
| **WAN5** | `41.49.132.208` | `255.255.255.252` | `41.49.132.209` | `41.49.132.210` | `41.49.132.211` | 2 |
| **WAN6** | `41.49.132.212` | `255.255.255.252` | `41.49.132.213` | `41.49.132.214` | `41.49.132.215` | 2 |
| **WAN7** | `41.49.132.216` | `255.255.255.252` | `41.49.132.217` | `41.49.132.218` | `41.49.132.219` | 2 |

---

