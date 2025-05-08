---
date: 2025-04-28T13:31:43+05:30
title: "Full Network Addressing Architecture for Hybrid Infrastructure"
lastmod: 2025-04-28
description: >
  A hierarchical and scalable IP addressing strategy for baremetal, Proxmox VMs,
  container networks, and edge/mobile systems with hostname conventions and subnet planning.
categories:
  - Infrastructure
  - Networking
  - Virtualization
  - Architecture
tags:
  - IP Addressing
  - Proxmox
  - OPNsense
  - Docker Networking
  - Termux
  - DNS Strategy
series: ["Hybrid Infrastructure Design"]
draft: false
slug: "hybrid-network-ip-architecture"
toc: true
aliases:
  - /networking/hybrid-infra-architecture/
---

# 📡 Full Network Addressing Architecture for Hybrid Infrastructure

---

## 1. 🎯 Concept Overview

This document defines a highly structured, hierarchical IP addressing and hostname convention for a multi-environment infrastructure that includes:

- Baremetal systems (e.g., Arch Linux on `sitar-1-arch`)
- Virtualized systems (e.g., Proxmox VMs, OPNsense appliances)
- Containerized services (e.g., Docker networks)
- Mobile-edge systems (e.g., Termux-based clients or gateways)
- Future cloud or experimental research subnets

The network design is **hierarchical**, **incremental**, and **self-documenting**, using a `w.x.y.z` IP structure and FQDN conventions for every entity on the network.

---

## 2. 🧭 Use Cases and Motivation

The design enables:

- Running multiple **Proxmox clusters** on a single baremetal host
- Internal routing using **OPNsense** appliances per virtual cluster
- Controlled **Docker container networks** per VM
- **Peer-to-peer** or **VPN-connected clusters** using WireGuard or similar tooling
- Support for **failover networking** via DHCP when static assignment fails
- Clear **resource isolation**, **debugging**, and **DNS integration**
- Future-proofed segments for **mobile**, **research**, and **nested deployments**

This structure is critical for deployments where **IP conflicts, misconfigurations, or lack of traceability** could lead to major downtime or security risks.

---

## 3. 🧠 IP Structure and Addressing Philosophy

We use a 4-octet model: `w.x.y.z`.

Each octet has a **purpose**, allowing every address to be instantly understandable by a human or automation:

| Octet | Meaning             | Scope / Origin                              |
|-------|---------------------|---------------------------------------------|
| `w`   | Network Group ID     | Top-level domain: baremetal, virtual, termux |
| `x`   | VM-level Network ID  | Per-VM internal network space               |
| `y`   | Docker Subnet ID     | Internal Docker network on that VM         |
| `z`   | Host Address         | Actual device/container/service IP          |

This allows you to pinpoint:
- Where an IP lives (physical or virtual)
- What type of service it is
- What its parent is (host → VM → container)

---

## 4. 🧩 Per-Octet Breakdown (`w.x.y.z`)

### 🔹 `w` — Network Group ID

Defines the **top-level environment** of the node:

| Range       | Description                       |
|-------------|-----------------------------------|
| `11–99`     | Baremetal networks                |
| `100–199`   | Virtualized networks (Proxmox, etc.) |
| `200–250`   | Android-based networks (Termux, Android VMS)   |
| `251–254`   | Research, staging, or future-reserved |
| `10`        | Special use for NAT `/29` subnets |

- `w` is the **backbone layer**: every environment starts here.
- Reserved `w` values allow long-term planning and portable policies.

---

### 🔸 `x` — VM Network ID

Defines the **VM's internal networking space**.

- Assigned **incrementally per VM**, whether it’s a hypervisor or not.
- Reserved **upon creation** of a VM to avoid reuse and clashes.
- Encourages deterministic mapping from VM to IP.
  
Example:
- First VM on `sitar-1-arch` → `x = 1`
- Second VM → `x = 2`

VMs that don’t run Docker or don’t expose networks still get an `x` reserved.

---

### 🔸 `y` — Docker Network ID

Defines **internal Docker bridges** on a per-VM basis.

- Docker may define multiple virtual networks (e.g., `lan1`, `lan2`, `backend`, `frontend`)
- Each one gets an incrementally assigned `y`:
  - First network → `y = 1`
  - Second network → `y = 2`

This guarantees:
- No collisions between networks even on the same VM
- Clear traceability from container to Docker host and VM

---

### 🔸 `z` — Final Host Address

- Assigned **incrementally per subnet**.
- Typically reserved in the lower ranges for core infrastructure and admin services.
- **Statically configured** when possible; fallback to **DHCP** for fault tolerance.

Example:
- `w.x.y.5` → The fifth assigned container or service in that Docker subnet
- `w.x.0.z` → Host-level devices inside the VM

---

## 5. 🌐 Hostname & DNS Strategy

All nodes (VMs, containers, physical hosts) follow a DNS structure:

```
<service>.<pve-index>.<baremetal-host>.<environment>.rohanbatra.in
```

### Example:
```
pihole.pve-1.sitar-1-arch.production.rohanbatra.in
vpn.pve-2.sitar-1-arch.lab.rohanbatra.in
```

Benefits:
- DNS reflects hierarchy and IP origin
- Great for observability, automation, and access control
- Makes reverse DNS trivial to configure

---

## 6. 🧪 Real-World Example: 2 Proxmox VMs with OPNsense

Let’s assume:

- Host: `sitar-1-arch`
- Proxmox VM1 hosts `pihole`, `vpn`
- Proxmox VM2 hosts `web`, `dns`

### Assignments:

| Component        | IP                          | Description                    |
|------------------|------------------------------|--------------------------------|
| Host             | `12.0.0.1`                   | Baremetal device               |
| VM1              | `101.1.0.1`                  | Proxmox VM1                    |
| OPNsense in VM1  | `101.1.0.2`                  | Routing for VM1                |
| Docker LAN1      | `101.1.1.0/24`               | First Docker network on VM1    |
| Pihole           | `101.1.1.5`                  | First container in lan1        |
| VPN              | `101.1.1.6`                  | Second container               |
| VM2              | `102.2.0.1`                  | Proxmox VM2                    |
| OPNsense in VM2  | `102.2.0.2`                  | Routing for VM2                |
| Docker LAN1      | `102.2.1.0/24`               | First Docker network on VM2    |

> "The above table is not yet updated, but it will be soon. I'm aware that VM1 and VM2 are supposed to be using NAT addresses in the 10.x.y.z range; however, the table currently reflects a configuration that has not yet been implemented."

---

## 7. 📦 Subnet Planning Strategy

For subnets and NAT-ed networks, `/29` is used:

- Each `/29` subnet gives **6 usable IPs**
- Used for VMs that need 4 IPs (e.g., 2 Proxmox + 2 OPNsense)
- Example:
  ```
  Subnet: 192.168.100.0/29
  Usable IPs: 192.168.100.1 to 192.168.100.6
  Broadcast: 192.168.100.7
  ```

Subnets are reused logically per virtual network, keeping overlap impossible.

---

## 8. 🔁 Redundancy, DHCP & Failover Strategy

- All nodes are assigned **static IPs** for reliability and discoverability.
- **DHCP fallback** is configured per subnet:
  - If a node loses its static config, it can still communicate.
  - DHCP range avoids static addresses.

- Proxmox networks are backed by XML definitions with reserved ranges:
  ```xml
  <range start='192.168.100.2' end='192.168.100.5'/>
  ```

---

## 9. 📦 Reserved Ranges & Future-Proofing

| Range       | Use Case                      |
|-------------|-------------------------------|
| 10.x.x.x    | NAT-ed `/29` networks          |
| 11–99       | Physical hosts, reverse proxies|
| 100–199     | Virtual machines & clusters    |
| 200–250     | Termux/Mobile/Edge nodes       |
| 251–254     | Reserved for research/future   |

This ensures the architecture can grow across:
- Datacenters
- Mobile deployments
- Campus/edge clusters
- VPN federation or multi-tenant scenarios

---

## 10. 🖼️ Visual Topology (Example)

we may represent the structure like this in a diagram:

```
[ Baremetal: sitar-1-arch (w=12) ]
        |
        +--> [ VM1 (x=1) ]
        |       +--> Docker LAN1 (y=1): 12.1.1.0/24
        |       +--> Docker LAN2 (y=2): 12.1.2.0/24
        |
        +--> [ VM2 (x=2) ]
                +--> Docker LAN1 (y=1): 12.2.1.0/24
```

"The above diagram is also not yet updated, but it will be soon. The diagram currently shows a setup that hasn't been implemented yet."

