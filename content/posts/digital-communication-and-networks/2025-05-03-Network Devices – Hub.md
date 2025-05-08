---
title: "Network Devices – Hub"
date: 2025-05-03T13:37:21+05:30
draft: false
tags: ["networking", "unit1", "devices", "hub", "physical"]
categories: ["Digital Communication and Computer Networks"]
---

# 🔌 Network Device: Hub

A **Hub** is a basic networking device that operates at **Layer 1 (Physical Layer)** of the OSI model. It is used to connect multiple devices in a **LAN** (Local Area Network) by broadcasting data to all connected devices.

---

## 🔹 What is a Hub?

A **Hub** is a simple, non-intelligent device that connects multiple computers or devices within a LAN. Unlike a switch or bridge, a hub does not filter or direct traffic based on MAC or IP addresses. It **broadcasts incoming data to all ports**, regardless of the destination, which can lead to inefficiencies in larger networks.

---

## 🔹 How Does a Hub Work?

1. **Broadcasting**: When a device sends data to the hub, the hub sends the data to all connected devices, not just the intended recipient.
2. **No Addressing**: The hub doesn’t examine data to see where it should go, unlike a switch or router that reads MAC or IP addresses.
3. **Collision Domains**: All ports on a hub belong to the same collision domain, meaning if two devices transmit at the same time, data collisions can occur, leading to inefficiency and delays.

---

## 🔹 Types of Hubs

| Type            | Description |
|-----------------|-------------|
| **Active Hub**  | Regenerates signals before broadcasting them to connected devices. |
| **Passive Hub** | Simply forwards data without amplification, often used for small networks. |
| **Intelligent Hub** | Provides additional functionality such as network monitoring, device management, and sometimes Power over Ethernet (PoE). |

---

## 🔹 Hub vs. Other Devices

| Feature         | Hub                      | Switch                  | Router                   |
|------------------|--------------------------|--------------------------|--------------------------|
| OSI Layer        | Layer 1 (Physical)        | Layer 2 (Data Link)      | Layer 3 (Network)        |
| Data Forwarding  | Broadcasts to all ports   | Forwards data based on MAC addresses | Routes data based on IP addresses |
| Primary Role     | Simple data distribution  | Intelligent data forwarding | Inter-network routing     |
| Collision Domain | One collision domain for all ports | Separate collision domains for each port | No collision domain – uses routing |

---

## 🔹 Key Hub Functions

1. **Signal Repetition**: Hubs repeat signals to extend the range of the network. They are useful for connecting devices over long distances.
2. **Data Broadcasting**: Hubs broadcast data to all connected devices, which can lead to network inefficiency.
3. **No Filtering**: Hubs do not filter data based on addresses, which means all devices receive all transmitted data.
4. **Basic Network Connectivity**: Hubs provide basic connectivity and are most useful in smaller networks with few devices.

---

## 🛠️ Common Use Cases

- **Small Office/Home Office Networks**: Hubs can be used in small networks where efficiency is not a major concern.
- **Expanding Network Size**: Hubs can be used to expand a small network by adding more devices, though they are less efficient than switches.
- **Signal Regeneration**: In networks that require signal boosting over longer distances, hubs can regenerate signals.

---

## 🔹 Hub in OSI & TCP/IP Models

| OSI Layer | Role of Hub |
|-----------|-------------|
| **Layer 1** | A physical device that transmits data without filtering or forwarding intelligently |

---

## 📝 Summary

Hubs are basic devices that operate at the physical layer of the OSI model. They serve to broadcast data to all connected devices and are useful in small networks. However, their lack of intelligence in managing traffic makes them inefficient compared to more advanced devices like switches, which provide better performance and network segmentation.

---

**Next Up:** Repeaters, Modems, and Other Physical Layer Devices
