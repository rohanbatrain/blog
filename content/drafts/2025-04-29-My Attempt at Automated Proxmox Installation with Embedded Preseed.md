---
date: 2025-04-29T17:05:43+05:30
title: "My Quest for Hands-Free Proxmox: An Incomplete Attempt at Automated Bliss via Embedded Preseed"
lastmod: 2025-04-29
description: >
  An uncompleted attempt to fully automate Proxmox VE installation in VirtManager on Arch Linux by embedding a preseed file into a custom ISO, detailing the process and the challenges encountered.
categories:
  - Virtualization
  - Automation
  - Proxmox
  - Linux
  - Incomplete
tags:
  - Proxmox
  - VirtManager
  - Preseed
  - Automated Installation
  - Arch Linux
  - Incomplete Attempt
  - Automation Incomplete
  - Preseed Issues

draft: true
slug: "proxmox-auto-install-preseed-virtmanager-incomplete"
toc: true
aliases:
  - /proxmox/automated-install-embedded-preseed-incomplete/
---

## My Quest for Hands-Free Proxmox: An **Incomplete** Attempt at Automated Bliss via Embedded Preseed

Hey everyone! Today, I wanted to recount a recent, and ultimately **uncompleted**, foray into the realm of virtualization automation. My ambition? To achieve a completely unattended installation of Proxmox VE within VirtManager on my trusty Arch Linux machine. The vision was clear: craft a custom ISO with a preseed file meticulously integrated, initiate a VM, and witness Proxmox install itself autonomously, requiring zero manual input. Sounds like a dream, doesn't it? Well, the journey proved to be quite… enlightening in its lack of completion.

### The Ambitious, Yet **Unfinished**, Plan

The central idea was to harness Proxmox's preseed functionalities. For those unfamiliar, a preseed file empowers you to provide answers to all the installer prompts beforehand, facilitating a fully automated setup. Instead of manually configuring language, keyboard layout, disk partitioning, and so forth, the installer gleans these details from the preseed file.

My strategy involved directly embedding this preseed file into a modified Proxmox ISO. The theory was that upon booting the VM from this tailored ISO, the installer would detect the preseed and proceed seamlessly. To bring this aspiration to fruition, I equipped myself with a Bash script.

### Diving into the Script (and the Anatomy of an **Unfinished Task**)

My script (presented below in its entirety) was designed to execute several key tasks:

1.  **Dependency Verification:** First and foremost, it checked for the presence of essential tools such as `qemu-img`, `genisoimage`, and `virt-install`. You can't build without the necessary instruments!
2.  **ISO Dissection:** I mounted the original Proxmox ISO and copied its contents to a working directory. Think of it as preparing the patient for surgery.
3.  **Preseed Transplantation (Theoretically):** The critical step – copying my `answer.toml` preseed file into the root directory of the ISO's file structure. This was intended to be the installer's source of truth.
4.  **Bootloader Persuasion (The Crucial **Unfinished Step**):** This is where I attempted to inform the bootloader about the preseed file. I diligently modified both `isolinux.cfg` (for legacy BIOS boot) and `grub.cfg` (for modern UEFI boot) to include the kernel parameter: `preseed/file=/cdrom/answer.toml auto=true priority=critical`. This was meant to instruct the installer, "Hey, the answers are on the CD-ROM, and they're important!" **However, this is where things seemed to fall short, as the installer stubbornly ignored these parameters.**
5.  **The Genesis of a Flawed ISO:** Using `genisoimage`, I then crafted a new ISO file, effectively a customized Proxmox installer with my preseed "baked in."
6.  **Virtual Hardware Configuration:** I provisioned a virtual disk for the Proxmox VM using `qemu-img`.
7.  **Launching the **Unsuccessful** Automation:** Finally, I employed `virt-install` to create and boot the VM, directing it to my custom ISO and allocating the required resources. The `--noautoconsole` option was crucial – the aim was zero manual interaction.
8.  **Cleanup and Post-Mortem:** Tidying up the temporary files and checking the VM's status were the final steps in this **uncompleted endeavor**.

```bash
#!/bin/bash
# ────────────────────────────────────────────────────────────────────────────────
#  ██████╗      ██████╗     ██╗  ██╗     █████╗     ███╗   ██╗
# ██╔══██╗    ██╔═══██╗    ██║  ██║    ██╔══██╗    ████╗  ██║
# ██████╔╝    ██║   ██║    ███████║    ███████║    ██╔██╗ ██║
# ██╔══██╗    ██║   ██║    ██╔══██║    ██╔══██║    ██║╚██╗██║
# ██║  ██║    ╚██████╔╝    ██║  ██║    ██║  ██║    ██║ ╚████║
# ╚═╝  ╚═╝     ╚═════╝     ╚═╝  ╚═╝    ╚═╝  ╚═╝    ╚═╝  ╚═══╝
#
#  🛠️ Author: Rohan Batra (@Rohanbatrain)
#  📜 Script: Fully Automate Proxmox VE Installation with Embedded Preseed
# ────────────────────────────────────────────────────────────────────────────────

set -euo pipefail

# ── Configuration ─────────────────────────────────────────────
VM_NAME="pve-1"
DISK_PATH="/var/lib/libvirt/images/${VM_NAME}.qcow2"
RAM="4096"
VCPUS="2"
DISK_SIZE="32"
NETWORK="nat-1"
ISO_ORIGINAL="/home/rohan/Templates/proxmox-ve_8.4-1.iso"
WORK_DIR="<span class="math-inline">HOME/proxmox\-iso"
PRESEED\_SOURCE\="/home/rohan/Templates/Preseeds/</span>{VM_NAME}/answer.toml"
ISO_FINAL="/home/rohan/Templates/proxmox-ve_8.4-1-preseed.iso"
OS_VARIANT="debian10"

# ── Dependencies ─────────────────────────────────────────────
echo -e "\n\033[1;36m🔍 Checking for required tools...\033[0m"
for cmd in qemu-img genisoimage virt-install; do
  if ! command -v $cmd &>/dev/null; then
    echo -e "\033[1;31m❌ Missing: $cmd. Please install it.\033[0m"
    exit 1
  fi
done
echo -e "\033[1;32m✅ All dependencies are available.\033[0m"

# ── Step 1: Prepare Working ISO ──────────────────────────────
echo -e "\n\033[1;36m📁 Preparing modified ISO with embedded preseed...\033[0m"

mkdir -p "$WORK_DIR"
sudo mount -o loop "$ISO_ORIGINAL" /mnt
cp -rT /mnt "$WORK_DIR"
sudo umount /mnt

# Copy preseed file
cp "$PRESEED_SOURCE" "$WORK_DIR/answer.toml"

# Modify isolinux config for BIOS boot
ISOLINUX_CFG="$WORK_DIR/boot/isolinux/isolinux.cfg"
if grep -q "append" "<span class="math-inline">ISOLINUX\_CFG"; then
sed \-i '/append/s/</span>/ preseed\/file=\/cdrom\/answer.toml auto=true priority=critical/' "$ISOLINUX_CFG"
fi

# Modify GRUB config for UEFI boot
GRUB_CFG="$WORK_DIR/boot/grub/grub.cfg"
if grep -q "linux" "<span class="math-inline">GRUB\_CFG"; then
sed \-i '/linux/s/</span>/ preseed\/file=\/cdrom\/answer.toml auto=true priority=critical/' "$GRUB_CFG"
fi

# Create new ISO
genisoimage -o "$ISO_FINAL" \
  -b boot/isolinux/isolinux.bin -c boot/isolinux/boot.cat \
  -no-emul-boot -boot-load-size 4 -boot-info-table \
  -J -R -V "PROXMOX_AUTO" "$WORK_DIR"

echo -e "\033[1;32m✅ Preseed ISO created: $ISO_FINAL\033[0m"

# ── Step 2: Create VM Disk ───────────────────────────────────
echo -e "\n\033[1;36m💾 Creating VM disk...\033[0m"
if [ ! -f "$DISK_PATH" ]; then
  sudo qemu-img create -f qcow2 "<span class="math-inline">DISK\_PATH" "</span>{DISK_SIZE}G"
  echo -e "\033[1;32m✅ Disk created at $DISK_PATH\033[0m"
else
  echo -e "\033[1;33mℹ️ Disk already exists at $DISK_PATH\033[0m"
fi

# ── Step 3: Create Proxmox VM ────────────────────────────────
echo -e "\n\033[1;36m🚀 Launching Proxmox VM with embedded preseed...\033[0m"
sudo virt-install \
  --name "$VM_NAME" \
  --ram "$RAM" \
  --vcpus "$VCPUS" \
  --os-variant "$OS_VARIANT" \
  --disk path="$DISK_PATH",format=qcow2,bus=virtio \
  --cdrom "$ISO_FINAL" \
  --network network="$NETWORK",model=virtio \
  --graphics spice \
  --console pty,target_type=serial \
  --boot uefi \
  --cpu host-passthrough \
  --noautoconsole

echo -e "\033[1;32m✅ Proxmox VM '$VM_NAME' created and started.\033[0m"

# ── Step 4: Cleanup ──────────────────────────────────────────
echo -e "\n\033[1;36m🧹 Cleaning up temporary files...\033[0m"
rm -rf "$WORK_DIR"
echo -e "\033[1;32m✅ Cleanup done.\033[0m"

# ── Step 5: Show VM Status ───────────────────────────────────
echo -e "\n\033[1;36m📋 Current VM status:\033[0m"
sudo virsh list --all
```

## The Lingering Questions (and a Touch of Incompletion)

While the script itself executed without major hiccups, the core objective – a fully automated, hands-free installation – remained unachieved. I suspect the issue lies in how the Proxmox installer handles embedded preseed files, or perhaps there's a subtle nuance in the bootloader configuration that I've overlooked.

This attempt, while ultimately not fully successful in achieving its primary goal, was nonetheless a valuable learning experience. It highlighted the complexities involved in fully automating OS installations and the potential discrepancies between documentation and actual behavior.

The quest for truly hands-free Proxmox in VirtManager continues, and I'll be sure to share any future breakthroughs (or further incomplete endeavors!). Stay tuned!

## FUTURE ROHAN 

This was fixed or achieved by my project -> proxmox auto installer docker