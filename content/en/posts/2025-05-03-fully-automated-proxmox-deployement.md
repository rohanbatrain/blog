---
date: 2025-05-03T00:31:19+05:30
title: "Proxmox Automated VM Builder with Dual Disks"
author: "Rohan Batra"
description: "Automate custom Proxmox ISO builds using answer.toml files and provision virtual machines with two identical disks via libvirt and virt-install."
summary: "End-to-end automation of Proxmox ISO customization and VM provisioning using Docker and libvirt with support for dual QCOW2 disks."
keywords: ["Proxmox", "Virtualization", "Automation", "Libvirt", "virt-install", "Infrastructure as Code", "qemu", "bash"]
tags: ["Proxmox", "Automation", "VM", "Libvirt", "QEMU", "Bash"]
categories: ["Infrastructure", "DevOps", "Virtualization", "Homelab"]
slug: "proxmox-vm-builder-dual-disks"
readingTime: 6
showToc: true
tocOpen: true
draft: false
type: "docs"
---


## 📘 Proxmox Automated VM Builder with Dual Disks

This script automates the following:

1. Verifies the environment and required files.
2. Builds customized Proxmox ISO images using answer files.
3. Provisions virtual machines using those ISOs with **two identical virtual disks** for each VM.

---

## 🧰 Prerequisites

Ensure the following tools and dependencies are available:

* `bash` (script written for Bash shell)
* `docker` (to run the ISO customization container)
* `virt-install` (from the `virt-manager` suite)
* `qemu-img` (for creating QCOW2 disk images)
* `libvirt` (for VM creation and management)
* Required user permissions (sudo access for VM and disk operations)
* A Proxmox VE ISO (version 8.4 in this script)

---

## 🗂️ Directory Structure

```
.
├── iso/
│   ├── proxmox-ve_8.4-1.iso
│   └── output/
├── secrets/
│   └── <profile_name>/
│       └── answer.toml
└── build.sh  ← (this script)
```

---

## 🧩 Configuration

The script defines several configurable parameters:

| Variable      | Description                                     |
| ------------- | ----------------------------------------------- |
| `ISO_VERSION` | Proxmox ISO version number                      |
| `ISO_BASE`    | Name of the base ISO file                       |
| `ISO_DIR`     | Directory to store the base ISO and outputs     |
| `ANSWERS_DIR` | Path to the profile directories                 |
| `OUTPUT_DIR`  | Directory where custom ISOs will be placed      |
| `OS_VARIANT`  | libvirt OS variant (`debian10` for Proxmox 8.x) |
| `RAM`         | RAM allocated to the VM (in MB)                 |
| `VCPUS`       | Number of virtual CPUs for each VM              |
| `DISK_SIZE`   | Size (in GB) of each disk (two disks per VM)    |
| `NETWORK`     | libvirt network to attach to                    |

---

## 🛠️ What the Script Does

### 1. Ensures Required Directories Exist

Creates the `iso`, `secrets`, and `iso/output` folders if they do not exist.

### 2. Verifies ISO and Answer Files

* Ensures the Proxmox base ISO exists.
* Looks for `answer.toml` files in `./secrets/*/`.

Each directory under `secrets` represents a **profile** that defines the configuration for a VM.

### 3. Builds Custom ISOs per Profile

For each profile, it calls the Dockerized Proxmox Auto Install Assistant with:

```bash
docker run \
  -v <ISO_DIR>:/iso:ro \
  -v <ANSWERS_DIR>:/answers:ro \
  -v <OUTPUT_DIR>:/out \
  rohanbatra/proxmox-auto-install-assistant-docker:latest \
    "/iso/${ISO_BASE}" "$profile"
```

This generates an auto-install ISO for that profile.

### 4. Creates VMs with Two Disks

For each profile:

* It creates two QCOW2 virtual disks named:

  * `<profile>_disk_1.qcow2`
  * `<profile>_disk_2.qcow2`
* Uses `virt-install` to create the VM with:

  * VNC graphics
  * UEFI boot
  * 2 disks
  * Proxmox ISO attached
  * NAT-based networking

### 5. Shows Final VM Status

At the end, it runs `sudo virsh list --all` to show all VMs and their current state.

---

## 🖥️ Example: Adding a Profile

To create a new VM profile:

```bash
mkdir -p secrets/webserver
cp answer_template.toml secrets/webserver/answer.toml
```

Edit `answer.toml` to customize the installation.

---

## 💡 Tips

* Make sure the `answer.toml` matches the required format for the Proxmox Auto Installer.
* You can boot VMs using VNC (e.g., `virt-viewer` or `virt-manager`).
* To delete a VM:

  ```bash
  sudo virsh destroy <vm-name>
  sudo virsh undefine <vm-name>
  sudo rm /var/lib/libvirt/images/<vm-name>_disk_*.qcow2
  ```

---

## 📜 Full Script

```bash
set -euo pipefail

# ─── Config ─────────────────────────────────────────────────────
ISO_VERSION="8.4"
ISO_BASE="proxmox-ve_${ISO_VERSION}-1.iso"
ISO_DIR="./iso"
ANSWERS_DIR="./secrets"
OUTPUT_DIR="${ISO_DIR}/output"
OS_VARIANT="debian10"
RAM="4096"
VCPUS="2"
DISK_SIZE="32"
NETWORK="nat-1"

# ─── Ensure Required Directories Exist ──────────────────────────
for dir in "$ISO_DIR" "$ANSWERS_DIR" "$OUTPUT_DIR"; do
    [ ! -d "$dir" ] && echo "📁 Creating $dir" && mkdir -p "$dir"
done

# ─── Prompt if ISO or .toml Files Are Missing ───────────────────
if [ ! -f "${ISO_DIR}/${ISO_BASE}" ]; then
    echo "❌ Missing base ISO: ${ISO_DIR}/${ISO_BASE}"
    echo "➡️  Please download and place it in ${ISO_DIR}"
    exit 1
fi

PROFILES=()
for answer_file in "${ANSWERS_DIR}"/*/answer.toml; do
    [ -f "$answer_file" ] || continue
    profile=$(basename "$(dirname "$answer_file")")
    PROFILES+=("$profile")
done

if [ ${#PROFILES[@]} -eq 0 ]; then
    echo "❌ No profiles found in ./secrets/*/answer.toml"
    echo "➡️  Please create at least one profile folder and put answer.toml inside"
    exit 1
fi

# ─── Build Custom ISOs ──────────────────────────────────────────
for profile in "${PROFILES[@]}"; do
    echo -e "\n🛠️ Building ISO for profile: ${profile}"
    
    docker run --rm \
      -v "$(realpath $ISO_DIR):/iso:ro" \
      -v "$(realpath $ANSWERS_DIR):/answers:ro" \
      -v "$(realpath $OUTPUT_DIR):/out" \
      rohanbatra/proxmox-auto-install-assistant-docker:latest \
        "/iso/${ISO_BASE}" "$profile"
done

# ─── Create VMs from ISOs ───────────────────────────────────────
for profile in "${PROFILES[@]}"; do
    VM_NAME="$profile"
    DISK_PATH_1="/var/lib/libvirt/images/${VM_NAME}_disk_1.qcow2"
    DISK_PATH_2="/var/lib/libvirt/images/${VM_NAME}_disk_2.qcow2"
    ISO_PATH="${OUTPUT_DIR}/proxmox-ve_${ISO_VERSION}-auto-${profile}.iso"

    echo -e "\n💻 Creating VM: ${VM_NAME}"

    if [ ! -f "$ISO_PATH" ]; then
        echo "❌ ISO not found for ${profile} at $ISO_PATH. Skipping VM creation."
        continue
    fi

    # Create both disks if missing
    for disk_path in "$DISK_PATH_1" "$DISK_PATH_2"; do
        if [ ! -f "$disk_path" ]; then
            echo "🪣 Creating disk at $disk_path..."
            sudo qemu-img create -f qcow2 "$disk_path" "${DISK_SIZE}G"
        fi
    done

    sudo virt-install \
      --name "$VM_NAME" \
      --ram "$RAM" \
      --vcpus "$VCPUS" \
      --os-variant "$OS_VARIANT" \
      --disk path="$DISK_PATH_1",format=qcow2,bus=virtio \
      --disk path="$DISK_PATH_2",format=qcow2,bus=virtio \
      --cdrom "$ISO_PATH" \
      --network network="$NETWORK",model=virtio \
      --graphics vnc \
      --noautoconsole \
      --boot uefi \
      --cpu host-passthrough

    echo "✅ VM '${VM_NAME}' created with ISO: $ISO_PATH and disks: $DISK_PATH_1, $DISK_PATH_2"
done

# ─── Final VM Status ────────────────────────────────────────────
echo -e "\n📋 VM Status:"
sudo virsh list --all