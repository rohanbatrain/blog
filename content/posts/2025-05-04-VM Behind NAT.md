---
title: "VM Behind NAT? No Problem with Reverse SSH"
date: 2025-05-04T00:55:00+05:30 
description: "Easily connect to a VM behind NAT from your host using a reverse SSH tunnel. This guide is tailored for setups where the VM runs as root and the host runs a user like rohan."
tags: ["networking", "ssh", "vm", "nat", "reverse ssh", "linux"]
categories: ["DevOps", "Networking"]
author: "Rohan Batra"
draft: false
---
## 🧩 VM Behind NAT?

### 🖥️ Scenario

* Your **VM** is running as `root` user.
* Your **host** machine has a user named `rohan`.
* The VM is behind NAT — it **can talk to the host**, but the **host can’t directly talk to the VM**.
* You want the **host** to be able to connect to the **VM** anyway.

No worries — you can use a **reverse SSH tunnel** to solve this!

---

### ✅ Goal

Allow your host (`rohan@host`) to SSH into your VM (`root@vm`) **even though the VM is behind NAT**.

---

### 🔧 Step-by-Step Guide

#### 1. **From the VM (as `root`) — Start the Reverse SSH Tunnel**

Run this command on your VM:

```bash
ssh -R 2222:localhost:22 rohan@host
```

* This means: "Hey host, open port `2222` on yourself and forward that to port `22` on *me* (the VM)."
* Now your host has a **doorway (port 2222)** that connects to the VM's SSH.

> Tip: You might be prompted for `rohan`'s password — that’s normal.

---

#### 2. **From the Host (as `rohan`) — Connect to the VM**

Once the reverse tunnel is running, SSH into the VM like this:

```bash
ssh -p 2222 localhost
```

That connects you to the VM via the tunnel, even though it’s hidden behind NAT.

---

### 📈 Result

* ✅ VM can always talk to the host (normal NAT behavior).
* ✅ Host can now talk to the VM via port `2222` — thanks to the reverse tunnel.
* ✅ No need to mess with NAT rules or port forwarding.

---

### 💡 Optional: Keep the Tunnel Alive Automatically

If you want the reverse tunnel to always be up, add this to the VM’s `~/.ssh/config` or a script:

```bash
ssh -N -R 2222:localhost:22 rohan@host -o "ServerAliveInterval 60"
```

Or use a systemd service or cron job to make it persistent.
