---
title: "Layered Network Protocol Architectures (OSI & TCP/IP)"
date: 2025-05-03T13:06:21+05:30
draft: false
tags: ["networking", "unit1", "protocols", "osi", "tcpip"]
categories: ["Computer Networks"]
---

# Layered Network Protocol Architectures: OSI and TCP/IP

Protocol architectures organize communication tasks into **layers**. Each layer handles a specific function, ensuring modularity, easier troubleshooting, and interoperability.

---

## 🔹 What is a Protocol Stack?

A **protocol stack** is a collection of network protocols layered to work together. Each layer performs a specific function and interacts with layers directly above and below.

---

## 🔹 OSI Model (Open Systems Interconnection)

The **OSI model** is a theoretical model developed by ISO to standardize networking.

### 🖼️ OSI Model Layers (Top to Bottom)

```
┌──────────────┐ 7. Application (e.g., HTTP, FTP)
│              │
├──────────────┤ 6. Presentation (e.g., Encryption, JPEG)
│              │
├──────────────┤ 5. Session (e.g., APIs, sockets)
│              │
├──────────────┤ 4. Transport (e.g., TCP, UDP)
│              │
├──────────────┤ 3. Network (e.g., IP, ICMP)
│              │
├──────────────┤ 2. Data Link (e.g., MAC, PPP)
│              │
└──────────────┘ 1. Physical (e.g., Ethernet cables, signals)
```

### ✳️ Function of Each Layer:

| Layer | Function | Example Protocols |
|-------|----------|-------------------|
| **7. Application** | User interface & service | HTTP, FTP, DNS |
| **6. Presentation** | Data formatting, encryption | SSL/TLS, JPEG |
| **5. Session** | Connection setup, sync | NetBIOS, RPC |
| **4. Transport** | Reliable transmission | TCP, UDP |
| **3. Network** | Logical addressing, routing | IP, ICMP |
| **2. Data Link** | MAC addressing, framing | Ethernet, ARP, PPP |
| **1. Physical** | Bits over medium | Cables, Wi-Fi signals |

### 🔹 Mnemonic to Remember

> **A**ll **P**eople **S**eem **T**o **N**eed **D**ata **P**rocessing

---

## 🔹 TCP/IP Model

The **TCP/IP model** is the real-world implementation and forms the foundation of the Internet.

### 🖼️ TCP/IP Layers

```
┌──────────────────────┐ 4. Application (HTTP, FTP, SMTP)
│                      │
├──────────────────────┤ 3. Transport (TCP, UDP)
│                      │
├──────────────────────┤ 2. Internet (IP, ICMP)
│                      │
└──────────────────────┘ 1. Network Access / Link (Ethernet, Wi-Fi)
```

### ✳️ TCP/IP vs OSI Layer Mapping

| OSI Layer       | TCP/IP Layer            |
|------------------|--------------------------|
| Application (7)  |                          |
| Presentation (6) |   → Application          |
| Session (5)      |                          |
| Transport (4)    |   → Transport            |
| Network (3)      |   → Internet             |
| Data Link (2)    |                          |
| Physical (1)     |   → Network Access       |

> 🔸 TCP/IP merges OSI layers into four practical layers.

---

## 🔹 Comparison: OSI vs TCP/IP

| Feature          | OSI Model             | TCP/IP Model           |
|------------------|------------------------|-------------------------|
| Developed by     | ISO                    | DoD (Department of Defense) |
| Layers           | 7                      | 4                       |
| Protocols        | Theoretical            | Practical/Implemented  |
| Usage            | Reference model        | Real-world networking  |
| Layer separation | Strict                 | Flexible               |

---

## 🔹 Benefits of Layering

- **Modularity**: Layers are independent.
- **Interoperability**: Vendors can create compatible products.
- **Troubleshooting**: Problems can be isolated per layer.
- **Scalability**: Easy to upgrade layers without affecting others.

---

## 🔹 Encapsulation Process

Encapsulation adds headers as data moves **down** layers (sender). Each layer wraps the data.

```
[Application Data]
      ↓
[App Header + Data]
      ↓
[Transport Header + Data]
      ↓
[Network Header + Data]
      ↓
[Data Link Header + Data + Trailer]
      ↓
[Physical Layer: Bits on wire]
```

On the **receiver** side, the reverse happens (decapsulation).

---

## 📝 Summary

Both OSI and TCP/IP models define how data is transmitted across networks using layered protocols. While OSI is a conceptual model, TCP/IP is the foundation of real-world networking. Understanding the layered architecture helps in designing, implementing, and troubleshooting network systems.

---

**Next Up:** `LAN, WAN, MAN, PAN, and LAN Topologies`
