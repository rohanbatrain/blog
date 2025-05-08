---
title: "Exposing Port 8006 from a VM Behind NAT using Reverse SSH Tunnel"
date: 2025-05-04T01:15:21+05:30
description: "How to access a web service running on a VM behind NAT from the host using reverse SSH tunneling, with port 8006 as a practical example."
tags: ["ssh", "nat", "networking", "reverse ssh", "proxmox", "linux", "vm"]
categories: ["Networking", "DevOps"]
author: "rohan"
---

In virtualized environments, it's common to have a **VM running behind NAT**, especially when using tools like QEMU, VirtualBox, or cloud labs. This setup means the **VM can reach the host**, but **the host cannot directly initiate connections to the VM** — including to web services like the Proxmox web GUI running on port `8006`.

Fortunately, this limitation is easy to bypass using **reverse SSH tunneling**.

---

## 🧠 Objective

We want to:
- Access a **web service** running on **port 8006** of a VM that is **behind NAT**.
- Reach it **from the host** without any port forwarding or special NAT rules.

---

## 🧱 Environment

- **VM OS:** Linux (SSH server running, root access)
- **Host user:** `rohan`
- **VM user:** `root`
- **Web service:** Running on VM at `http://localhost:8006` (e.g., Proxmox)

---

## 🔁 Step 1: Create a Reverse SSH Tunnel from the VM

On the **VM**, run the following command:

```bash
ssh -R 8006:localhost:8006 rohan@host
```

This command does the following:

* Tells the **host** to open port `8006` on its own `localhost`.
* Forwards any traffic coming to that port to the **VM’s** port `8006`.

> 🔐 You may be prompted for `rohan`'s password on the host. Use SSH keys for automation.

---

## 🌐 Step 2: Access the Web Service on the Host

Now, from the **host machine**, open your browser and visit:

```
http://localhost:8006
```

🎉 You’ll see the web interface of the VM’s service, tunneled securely and directly to the host.

---

## 🔁 Making the Tunnel Persistent

To ensure the tunnel stays up even after reboots or disconnects, use one of the following methods.

### Option A: `autossh` (Simple and Robust)

Install `autossh` on the VM:

```bash
sudo apt install autossh
```

Then run:

```bash
autossh -f -N -R 8006:localhost:8006 rohan@host
```

### Option B: `systemd` Service (Clean Boot-Time Setup)

Create a `systemd` service on the VM:

**File:** `/etc/systemd/system/reverse-ssh-tunnel.service`

```ini
[Unit]
Description=Reverse SSH Tunnel to Host (Port 8006)
After=network.target

[Service]
User=root
ExecStart=/usr/bin/ssh -N -R 8006:localhost:8006 rohan@host -o "ServerAliveInterval=60" -o "ExitOnForwardFailure=yes"
Restart=always
RestartSec=5

[Install]
WantedBy=multi-user.target
```

Then run:

```bash
systemctl daemon-reexec
systemctl enable --now reverse-ssh-tunnel.service
```

---

## 🔒 Security Notes

* This tunnel binds **only to `localhost`** on the host, making it accessible only from the host machine — not over the network.
* Avoid binding to `0.0.0.0` unless you configure a firewall and authentication.

---

## ✅ Summary

By using reverse SSH tunneling, we’ve:

* Enabled access to a web service on port `8006` running in a NAT’d VM
* Avoided complex NAT or router configurations
* Created a secure and optionally persistent setup

This method works for any port — not just 8006 — making it a great general-purpose tool for working with NAT’d machines.

---

Need help with tunnels for multiple ports, or setting up proxies for internet access? Drop a comment or reach out!
