---
title: "Introduction to Computer Networking Concepts"
date: 2025-05-03T13:03:21+05:30
draft: false
tags: ["networking", "unit1", "basics"]
categories: ["Digital Communication and Computer Networks"]
---

# Introduction to Computer Networking Concepts

Computer networking connects computing devices to enable data sharing and communication. This foundation supports services like the internet, file sharing, and cloud computing.

---

## 🔹 Purposes of Digital Communication and Computer Networks

- **Resource Sharing**: Access shared printers, files, storage.
- **Communication**: Email, chat, video conferencing.
- **Remote Access**: Control systems across locations.
- **Centralized Data**: Easier management and backups.
- **Efficiency**: Distributed workloads and services.

---

## 🔹 Types of Digital Communication and Computer Networks

| Network | Coverage Area | Example |
|--------|----------------|---------|
| **PAN** | Personal range (~10 meters) | Bluetooth headset |
| **LAN** | Building or campus | Home/office Wi-Fi |
| **MAN** | Citywide | University networks |
| **WAN** | Country or global | Internet |

### 🖼️ Textual Diagram - Network Scale

```
PAN < LAN < MAN < WAN
```

---

## 🔹 Network Components

- **End Devices**: Users' computers, phones.
- **Network Devices**:
  - **[Switch]({{< relref "2025-05-03-Network Devices – Switch.md" >}})**: Connects devices in a LAN (uses MAC address).
  - **[Router]({{< relref "2025-05-03-Network Devices – Router.md" >}})**: Connects different networks (uses IP).
  - **[Modem]({{< relref "2025-05-03-Network Devices – Modem.md" >}})**: Converts digital ↔ analog for ISP.
  - **[Hub]({{< relref "2025-05-03-Network Devices – Hub.md" >}})**: Broadcasts data to all ports (no intelligence).
  - **[Bridge]({{< relref "2025-05-03-Network Devices – Bridges.md" >}})**: Connects LAN segments, filters by MAC.
  - **[Repeater]({{< relref "2025-05-03-Network Devices – Repeater.md" >}})**: Regenerates weak signals.
  - **[Access Point]({{< relref "2025-05-03-Network Devices – Access Point.md" >}})**: Provides Wi-Fi access.
  - **[Network Interface Card (NIC)]({{< relref "2025-05-03-Network Devices – Network Interface Card.md" >}})**: Hardware to connect devices to a network.
  - **[Transceivers]({{< relref "2025-05-03-Network Devices – Transceivers.md" >}})**: Send and receive signals over media.
- **Transmission Media**:
  - **Wired**: Ethernet (Cat6), Fiber.
  - **Wireless**: Wi-Fi, 4G/5G, Bluetooth.


### 🖼️ Textual Diagram - Basic LAN Setup

```
[PC]---+
       |
[PC]---+--[SWITCH]---[ROUTER]---[INTERNET]
       |
[Printer]
```

---

## 🔹 Communication Modes

| Mode        | Description                          | Example         |
|-------------|--------------------------------------|-----------------|
| **Simplex** | One-way only                         | Keyboard to PC  |
| **Half Duplex** | Two-way, one at a time          | Walkie-talkies  |
| **Full Duplex** | Two-way, simultaneous           | Phone calls     |

### 🖼️ Textual Diagram - Duplex Modes

```
Simplex:      A ---> B
Half-Duplex:  A <--> B (one at a time)
Full-Duplex:  A <===> B (simultaneous)
```

---

## 🔹 Transmission Types

- **Unicast**: One-to-one
- **Broadcast**: One-to-all
- **Multicast**: One-to-selected
- **Anycast**: One-to-nearest

### 🖼️ Textual Diagram - Broadcast vs Unicast

```
Unicast:     [Sender] ---> [Receiver]

Broadcast:   [Sender] ---> [All Devices on Network]

Multicast:   [Sender] ---> [Group of Devices]

Anycast:     [Sender] ---> [Nearest Suitable Receiver]
```

---

## 🔹 Communication Models

- **Peer-to-Peer (P2P)**:
  - No central server.
  - All devices are equal.
  
  ```
  [PC1] <---> [PC2] <---> [PC3]
  ```

- **Client-Server**:
  - Central server serves many clients.

  ```
  [Client1]
      |
  [Client2] ---> [Server]
      |
  [Client3]
  ```

---

## 🔹 Performance Terms

| Term        | Description                                   |
|-------------|-----------------------------------------------|
| **Bandwidth** | Max data rate of a link (bits/sec)         |
| **Latency**   | Time taken for data to reach destination    |
| **Throughput**| Actual data delivered per unit time         |
| **Jitter**    | Variation in latency over time              |
| **Error Rate**| Ratio of corrupted to total bits sent       |

---

## 🔹 Advantages of Networking

- Centralized management and storage.
- Real-time communication.
- Cost-effective resource sharing.
- Flexible and scalable systems.

---

## 🔹 Common Challenges

- Network Security (unauthorized access, malware).
- Data collisions and congestion.
- Hardware/software compatibility.
- Maintenance and monitoring overhead.

---

## 📝 Summary

Computer networking is the backbone of modern communication. It enables seamless interaction, data access, and resource sharing across varied devices and scales. Understanding foundational elements is crucial before diving into protocol stacks and deeper layers.

---

**Next Up:** `Layered Network Protocol Architectures (OSI & TCP/IP)`
