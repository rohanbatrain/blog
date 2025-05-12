---
title: "2025 04 30 Rooting Waydroid"
date: 2025-04-30T01:41:26+05:30
draft: false
---

# 📱 Magisk + OpenGApps on Waydroid 11 – Extended Documentation

## Overview

This project enables running **Magisk** and **OpenGApps (Pico variant)** on **Waydroid 11** by modifying and adapting the [MagiskOnWSA](https://github.com/LSPosed/MagiskOnWSA) method to work within Waydroid's LXC container environment. It is tested on **ArchLinux**, **Fedora**, and likely works on **Ubuntu** as well.

The GitHub Actions workflow builds patched `system.img` and `vendor.img` files, injecting Magisk and OpenGApps directly into the Waydroid image. These images replace the stock system images in your Waydroid installation.

This repository originally belongs to [pagkly/MagiskOnWaydroid](https://github.com/pagkly/MagiskOnWaydroid), and I have **forked** it for my use.

---

## ⚙️ Features

- 🔒 **Magisk Integration** (root access for Android apps)
- 🌐 **OpenGApps Support** (Google services & Play Store)
- 📦 Supports most Magisk modules that **do not** rely on **Zygisk**
- ✅ Works with Magisk versions **24.1** and **24.3**

---

## ❗ Limitations

- ❌ **Zygisk is NOT working** (No ETA)
- ❌ Modules like **LSPosed, Riru, Shamiko** currently **do not function**
- ⚠️ **Magisk v24.2, 2420x, and some newer versions** may fail to initialize
- 🛑 **Magisk v23.0 or below is not supported** due to boot issues
- ❌ **SafetyNet cannot be passed** — similar to other emulators

---

## 📥 Installation Guide

### Step 1: Clean Old Waydroid Images

**WARNING**: This will erase all Android data, apps, and settings. Backup first.

```bash
waydroid session stop
sudo waydroid container stop
sudo systemctl stop waydroid-container.service
sudo umount -l /var/lib/waydroid/{data,rootfs}
sudo umount /usr/share/waydroid-extra/images/{system,vendor}.img
sudo rm -rf /var/lib/waydroid /home/.waydroid ~/waydroid ~/.share/waydroid ~/.local/share/applications/*aydroid* ~/.local/share/waydroid
sudo rm -rf /usr/share/waydroid-extra/images/*
```

---

### Step 2: Install Waydroid Dev Image

#### Arch Linux (AUR + `yay` example)
```bash
sudo pacman -Syuu
yay -S waydroid-image-dev
```

You may need a kernel that supports `ashmem` and `binder`:

```bash
# Examples:
sudo pacman -S linux-xanmod-anbox
# or: sudo pacman -S linux-zen
```

---

### Step 3: Build Patched Images via GitHub Actions

1. **Fork** the [MagiskOnWaydroid repo](https://github.com/pagkly/MagiskOnWaydroid)
2. Go to **Actions > Build WSA > Run Workflow**
3. Input:
   - Magisk version download URL
   - OpenGApps variant (e.g., `pico`)
   - Root method (`magisk`)
4. Wait for build to complete and download the **artifact (ZIP)**
5. Extract it to get `system.img` and `vendor.img`

---

### Step 4: Replace Images and Initialize Waydroid

```bash
# Replace the existing Waydroid system and vendor images
sudo cp system.img /var/lib/waydroid/images/system.img
sudo cp vendor.img /var/lib/waydroid/images/vendor.img

# Re-initialize Waydroid
sudo waydroid init
sudo systemctl restart waydroid-container.service
waydroid session start &
waydroid show-full-ui
```

---

### Step 5: Magisk Setup and Reboot (IMPORTANT)

Due to initialization quirks:

```bash
waydroid session stop

# First container restart (network may fail)
sudo systemctl restart waydroid-container.service
waydroid session start
waydroid session stop

# Second container restart (should fix Ethernet)
sudo systemctl restart waydroid-container.service
waydroid session start
waydroid show-full-ui
```

---

## ✅ Working Magisk Modules

- **Busybox NDK**
- **Magisk Hide Props Config**
- **Detach** (detach Play Store apps)

## 🔄 Updating Instructions

- **Update system/vendor images**: Rerun GitHub Action and replace images
- **Update Magisk version**: Same as above (choose version in Action)
- **Sync updated scripts**: Use `Fetch Upstream` in your forked repo

---

## 💡 FAQ

**Q: The downloaded zip size is smaller than shown?**  
A: GitHub displays uncompressed size. ZIP is compressed.

**Q: How to manually install a Magisk module?**  
```bash
adb push module.zip /data/local/tmp
adb shell su -c magisk --install-module /data/local/tmp/module.zip
```

**Q: Can I use Magisk 23.0?**  
A: No. Use Magisk **24.1** or **24.3** only.

**Q: Why isn’t Zygisk working?**  
A: Waydroid runs in an LXC container using the Linux host kernel. There’s no recovery/boot image to patch like on real Android or WSA. Zygote starts too early for Magisk to hook it.

---

## 🧠 Technical Insights

- Uses modified `init.rc` to load `magisk su` near UI start
- Unlike WSA, Waydroid lacks support for a patched kernel with embedded SU binaries
- Possible workaround involves loading SU binaries as a kernel module when LXC starts, but it may pose **security risks**

Contributions from **LXC experts** are welcome to improve this area.

---

## 🏷️ Credits

- [Waydroid](https://waydro.id)
- [Magisk](https://github.com/topjohnwu/Magisk)
- [OpenGApps](https://opengapps.org/)
- [MagiskOnWSA](https://github.com/LSPosed/MagiskOnWSA)
- WSA-Kernel-SU / MagiskOnEmu / MagiskOnEmulator
- Project Kokoro for remount implementation

---

## 🔗 Related Resources

- 📣 My [LinkedIn Post](https://www.linkedin.com/en/posts/rohanbatrain_waydroid-magisk-gapps-activity-7323073114135822336-kJiF?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAAEPqBh8BH-tPbYYhUC-OyGBT1KdD6_ebicY) 

---
