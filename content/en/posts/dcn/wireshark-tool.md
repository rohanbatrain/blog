---
date: 2025-05-12T18:08:09+05:30
title: "Wireshark Tool: Introduction and Usage"
tags: ["Wireshark", "Network Analysis", "Packet Sniffer", "Protocol Analysis"]
series: "Network Layer"
categories: ["Computer Networks"]
draft: false
---

### 🔍 What is Wireshark?

Wireshark is a **network protocol analyzer** that captures and inspects packets traveling over a network in real time. It provides detailed insights into the structure of each packet, making it an essential tool for troubleshooting, security analysis, and network optimization.

---

### ⚙️ Key Features

- **Packet Capture**: Capture network traffic from interfaces like Ethernet, Wi-Fi, or VPN.
- **Detailed Protocol Analysis**: Supports thousands of protocols (TCP, UDP, HTTP, DNS, etc.).
- **Filters**: Allows powerful filters to focus on specific protocols, hosts, or ports.
- **Reassembly**: Reassembles data streams (e.g., TCP streams) to show full conversation.
- **Statistics**: Provides graphs, tables, and summaries of packet data.

---

### 🚨 Common Use Cases

1. **Troubleshooting Network Issues**
   - Identify latency, packet loss, and retransmissions.
   - Inspect slow or failed connections.
   
2. **Security Analysis**
   - Detect malicious activity (e.g., DDoS, unauthorized access).
   - Analyze encrypted traffic (if keys are available).

3. **Performance Monitoring**
   - Measure network throughput.
   - Identify bottlenecks or congestion points.

---

### 🔧 Basic Usage

- **Start a Capture**: Select the network interface and start capturing.
- **Apply Filters**: Use display filters like `ip.addr == 192.168.1.1` or `tcp.port == 80` to zoom in on specific traffic.
- **Examine Packets**: Click on packets to inspect headers, payload, and metadata.
- **Analyze Streams**: Reconstruct conversations (e.g., TCP or HTTP sessions) for deeper analysis.

---

### 📈 Insights

Wireshark is **powerful but requires expertise** to interpret the vast amount of data it collects. It's used by network engineers, security professionals, and researchers for its ability to provide **fine-grained visibility** into network activities.

---

### 🔗 Links
- Previous: [Quality of Service (QoS)]({{< relref "quality-of-service.md" >}})

