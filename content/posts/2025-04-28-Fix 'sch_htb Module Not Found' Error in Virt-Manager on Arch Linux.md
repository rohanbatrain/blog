---
date: 2025-04-28T13:51:18+05:30
title: "Fix 'sch_htb Module Not Found' Error in Virt-Manager on Arch Linux"
draft: false
tags: ["virt-manager", "linux", "arch", "virtualization", "networking"]
categories: ["Linux", "Virtualization"]
description: "Quick guide to fixing the 'modprobe: FATAL: Module sch_htb not found' error in Virt-Manager networking on Arch Linux."
---

# Fix 'sch_htb Module Not Found' Error in Virt-Manager on Arch Linux

While setting up **virt-manager** on Arch Linux, I encountered the following error when trying to start the default network:

```bash
modprobe: FATAL: Module sch_htb not found in directory /lib/modules/6.14.3-arch1-1
```

This error prevented virtual machines from accessing the network through `virt-manager`.

---

## Cause

The `sch_htb` module (Hierarchical Token Bucket) is critical for network traffic shaping. If missing, it usually means:

- Kernel headers are missing.
- The current kernel lacks needed networking modules.

---

## Solution

Install the correct packages:

```bash
sudo pacman -S linux-zen-headers linux-lts
```

Then reboot:

```bash
sudo reboot
```

After reboot, check if the module is available:

```bash
sudo modprobe sch_htb
```

And verify your networks:

```bash
virsh net-list --all
```

---

## Optional: Set LTS Kernel as Default

Set Linux LTS as default in your bootloader, and regenerate GRUB config:

```bash
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

---

## Conclusion

Installing `linux-zen-headers` and `linux-lts` ensures important modules like `sch_htb` are available, fixing networking in `virt-manager` on Arch Linux.

Happy virtualizing! 🚀
