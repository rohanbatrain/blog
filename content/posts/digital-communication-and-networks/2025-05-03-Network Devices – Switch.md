---
title: "Network Devices – Switch"
date: 2025-05-03T13:18:21+05:30
draft: false
tags: ["networking", "unit1", "devices", "switch", "data link"]
categories: ["Computer Networks"]
---

# 🔌 Network Device: Switch

A **Switch** is a networking device that operates primarily at **Layer 2 (Data Link Layer)** of the OSI model, though some switches can also function at **Layer 3 (Network Layer)**.

---

## 🔹 What is a Switch?

A **Switch** is an intelligent device used in LANs to connect multiple devices (like computers, printers, and servers). It uses **MAC addresses** to forward data only to the intended recipient, making communication more efficient compared to hubs.

---
## 🔹 How Does a Switch Work?

1. **Learning**: The switch examines the **source MAC address** of each incoming frame and stores it in a **MAC address table** (a.k.a. forwarding table).
2. **Forwarding**:
   - If the **destination MAC address** is **known**, the switch forwards the frame to the specific port where the destination device is connected. This minimizes unnecessary traffic on other ports, enhancing network efficiency.
   - If the **destination MAC address** is **unknown**, the switch doesn't know which port to forward the frame to. In this case, the frame is **flooded to all ports** (except the port it came from), ensuring that the frame reaches the intended device. Once the destination device responds, the switch learns its MAC address and updates its MAC table for future use.
3. **Filtering**: Unicast, multicast, and broadcast frames are filtered according to the destination.


---

## 🔹 Types of Switches

| Type | Description |
|------|-------------|
| **Unmanaged** | Plug-and-play, no configuration required. Used in homes or small offices. |
| **Managed** | Offers advanced features (VLANs, QoS, SNMP). Used in enterprise networks. |
| **Layer 3 Switch** | Supports routing functions, works at Network Layer too. |
| **PoE Switch** | Powers devices like IP cameras and VoIP phones through Ethernet cables. |

---

## 🔹 Switch vs. Other Devices

| Feature         | Hub                     | Switch                  | Router                   |
|------------------|--------------------------|--------------------------|--------------------------|
| OSI Layer        | Layer 1 (Physical)        | Layer 2 (Data Link)      | Layer 3 (Network)        |
| Data Forwarding  | Broadcasts to all ports   | Uses MAC address table   | Uses IP address & routing table |
| Intelligence     | No                       | Medium (MAC aware)       | High (IP + Routing aware) |
| Efficiency       | Low                      | High                     | Very High                |

---

## 🔹 Switch Features

- **MAC Address Table**: Maps MAC addresses to ports.
- **Full Duplex Communication**: Devices can send/receive simultaneously.
- **Loop Prevention**: Uses protocols like **STP (Spanning Tree Protocol)**.
- **VLAN Support** (on managed switches): Segments networks logically.

---

## 🛠️ Common Use Cases

- Building **LANs** in offices or homes.
- Connecting devices in **data centers**.
- **VLAN segmentation** for security and traffic management.
- Enabling **Power over Ethernet** (PoE) for IP-based devices.

---

## 🔹 Switch in OSI & TCP/IP Models

| OSI Layer | Role of Switch |
|-----------|----------------|
| **Layer 2** | Reads MAC addresses, forwards frames |
| **Layer 3** *(optional)* | Performs IP routing (Layer 3 switch) |

---

## 📝 Summary

Switches are central to efficient LAN communication, replacing hubs for their intelligent frame forwarding based on MAC addresses. They reduce network congestion, enhance performance, and support modern networking features like VLANs, PoE, and loop prevention.

---

**Next Up:** Routers, Bridges, Hubs, and other Networking Devices
