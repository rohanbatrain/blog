---
title: "Running BlissOS in Docker"
date: 2025-04-27T02:40:59+05:30
draft: false
description: "A quick guide to running BlissOS using Dock-Droid in Docker with KVM acceleration on Arch Linux."
tags: ["Docker", "BlissOS", "Android", "QEMU", "KVM", "Virtualization"]
categories: ["Virtualization", "Android"]
---

> BlissOS in Docker, but no KernelSU yet. Here's the setup anyway!

## 🧰 Requirements

Install the necessary packages on **Arch Linux**:

```bash
sudo pacman -S qemu-full libvirt dnsmasq virt-manager bridge-utils flex bison iptables-nft edk2-ovmf xorg-xhost
```

Enable required services:

```bash
sudo systemctl enable --now libvirtd
sudo systemctl enable --now virtlogd
```

Enable KVM and ignore unsupported MSRs (helpful for Android VMs):

```bash
echo 1 | sudo tee /sys/module/kvm/parameters/ignore_msrs
sudo modprobe kvm
```

Allow local X access so the Docker container can show the GUI:

```bash
xhost +local:
```

## 🚀 Run BlissOS with Docker

Now launch the container:

```bash
docker run -it \
    --device /dev/kvm \
    -v /tmp/.X11-unix:/tmp/.X11-unix \
    -e "DISPLAY=${DISPLAY:-:0.0}" \
    -p 5555:5555 \
    sickcodes/dock-droid:latest
```

## ⚠️ Heads Up

The image currently **doesn't have KernelSU**, so root management tools won't work yet. Just a heads-up for anyone trying to use Magisk or KernelSU features.

---

> That’s it! You’re running Android (BlissOS-based) in Docker. KernelSU fans — maybe next time. ✌️

