---
title: "Network Devices – Bridge"
date: 2025-05-03T13:33:21+05:30
draft: false
tags: ["networking", "unit1", "devices", "bridge", "data link"]
categories: ["Digital Communication and Computer Networks"]
---

# 🔌 Network Device: Bridge

A **Bridge** is a networking device that operates at **Layer 2 (Data Link Layer)** of the OSI model. It is used to **connect two or more network segments** within a local area network (LAN), helping to filter traffic and reduce collisions.

---

## 🔹 What is a Bridge?

A **Bridge** is a device used to divide large networks into smaller segments. It helps in controlling traffic between segments, increasing the efficiency of network communications. Unlike a hub or a switch, which broadcasts data to all devices, a bridge forwards data only to the segment where the destination device is located, improving network performance.

---

## 🔹 How Does a Bridge Work?

1. **Learning**: The bridge learns the **MAC addresses** of devices on each network segment.
2. **Filtering**: It filters frames based on destination MAC addresses. If the destination device is on the same segment, it is not forwarded.
3. **Forwarding**: If the destination device is on a different segment, the bridge forwards the frame to the appropriate segment.

---

## 🔹 Types of Bridges

| Type          | Description |
|---------------|-------------|
| **Transparent Bridge** | Operates without requiring any changes to the network. It simply forwards frames between segments based on MAC addresses. |
| **Source Route Bridge** | Uses routing information contained within the data frames themselves to determine forwarding. |
| **Learning Bridge** | Learns and updates the MAC address table dynamically as it observes network traffic. |
| **Spanning Tree Bridge** | Uses the Spanning Tree Protocol (STP) to prevent network loops by disabling some paths in the network.

---

## 🔹 Bridge vs. Other Devices

| Feature         | Switch                  | Router                   | Bridge                 |
|------------------|--------------------------|--------------------------|------------------------|
| OSI Layer        | Layer 2 (Data Link)      | Layer 3 (Network)        | Layer 2 (Data Link)    |
| Forwarding Logic | Uses MAC addresses       | Uses IP addresses        | Uses MAC addresses     |
| Primary Role     | Segmentation and Filtering| Inter-network Routing     | Segmenting a large network into smaller parts |
| Loop Prevention  | Uses STP (Spanning Tree Protocol) | Uses routing protocols | Uses STP to prevent loops |

---

## 🔹 Key Bridge Functions

1. **Segmentation**: Bridges break up large networks into smaller segments, reducing traffic and collisions.
2. **Collision Domain Reduction**: By dividing networks, a bridge reduces the size of collision domains, improving network performance.
3. **Filtering**: Bridges only forward data to the appropriate segment, improving network efficiency.
4. **Loop Prevention**: Bridges use the **Spanning Tree Protocol (STP)** to detect and prevent loops, which can create network congestion.

---

## 🛠️ Common Use Cases

- **LAN Segmentation**: Bridging helps to divide a large LAN into smaller, more manageable segments.
- **Reducing Collisions**: By segmenting the network, bridges help reduce the chance of data collisions.
- **Improving Network Performance**: By limiting traffic to only the necessary segments, bridges increase overall network efficiency.
- **Linking Different Media Types**: A bridge can connect different types of network media, such as Ethernet to Wi-Fi.

---

## 🔹 Bridge in OSI & TCP/IP Models

| OSI Layer | Role of Bridge |
|-----------|----------------|
| **Layer 2** | Forwards data frames based on MAC addresses, helps segment the network into smaller collision domains |

---

## 📝 Summary

Bridges are used in networking to reduce traffic and improve efficiency by segmenting larger networks. They operate at the Data Link layer, using MAC addresses to filter and forward frames. With features like loop prevention and collision domain reduction, bridges are crucial in ensuring smooth and efficient network operation.

---

**Next Up:** Hubs, Repeaters, and Other Basic Networking Devices