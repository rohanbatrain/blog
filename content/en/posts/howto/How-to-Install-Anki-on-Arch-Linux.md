---
title: "How to Install Anki on Arch Linux"
date: 2025-05-08T21:37:45+05:30
draft: false
tags: ["Arch Linux","Anki","AUR","Snap","Hugo"]
categories: ["How-to"]
author: "Rohan Batra"
---

## 1. Prerequisites

Before you begin, ensure your system is up‑to‑date:

```bash
sudo pacman -Syu                                     # Update core system packages
sudo pacman -S base-devel git                       # Install build tools
```

If you plan to use Snap later, you’ll also need:

```bash
sudo pacman -S --needed go squashfs-tools
```

---

## 2. Method A: Installing via AUR

ArchWiki recommends using the AUR packages `anki` or `anki-bin`:

1. **Choose your helper** (we’ll use `yay` below):

   ```bash
   sudo pacman -S yay                                # Install yay from [community]
   ```

2. **Install the binary bundle** (no local build):

   ```bash
   yay -S anki-bin                                  # Binary AUR package :contentReference[oaicite:0]{index=0}
   ```

   Or, **build from source**:

   ```bash
   yay -S anki                                      # Compiled AUR package :contentReference[oaicite:1]{index=1}
   ```

3. **Run Anki**:

   ```bash
   anki
   ```

### 2.1 Troubleshooting AUR Builds

* **`aqt.run()` missing**
  After a Python upgrade, you may see:

  ```
  AttributeError: module 'aqt' has no attribute 'run'
  ```

  Fix by reinstalling the protobuf binding:

  ```bash
  sudo pacman -S python-protobuf --asdeps           # Rebuild dependency :contentReference[oaicite:2]{index=2}
  yay -S anki --rebuild                            # Force rebuild against new Python
  ```
* **Rust `rsbridge` compile error**
  If `makepkg -s` dies building the Rust bridge, ensure you have `rust` and `cargo` installed:

  ```bash
  sudo pacman -S rust cargo                         # Provides Rust toolchain :contentReference[oaicite:3]{index=3}
  yay -S anki                                      # Retry build
  ```

---

## 3. Method B: Official Tarball

Anki upstream only supports the Linux tarball. This method always matches the latest release:

1. **Download** the `.tar.zst` from AnkiWeb:

   ```bash
   cd ~/Downloads
   wget https://apps.ankiweb.net/anki-2.1.57-linux-qt6.tar.zst  # adjust version :contentReference[oaicite:4]{index=4}
   ```

2. **Install dependencies**:

   ```bash
   sudo pacman -S zstd libxcb-xinerama libxcb-cursor nss    # Required libs :contentReference[oaicite:5]{index=5}
   ```

3. **Extract & run installer**:

   ```bash
   tar xaf anki-*-linux-qt6.tar.zst
   cd anki-*-linux-qt6
   sudo ./install.sh                                       # Installs into /usr/local :contentReference[oaicite:6]{index=6}
   ```

4. **Launch**:

   ```bash
   anki
   ```

---

## 4. Method C: Snap Package

Snap isolates Anki and auto‑updates, with rollback support:

1. **Enable snapd**:

   ```bash
   git clone https://aur.archlinux.org/snapd.git
   cd snapd && makepkg -si                               # Build snapd from AUR :contentReference[oaicite:7]{index=7}
   sudo systemctl enable --now snapd.socket
   sudo ln -s /var/lib/snapd/snap /snap
   ```

2. **Install Anki**:

   ```bash
   sudo snap install anki-desktop                         # Official snap :contentReference[oaicite:8]{index=8}
   ```

3. **Run**:

   ```bash
   snap run anki-desktop
   ```

---

## 5. Post‑Install Tips

* **Add‑ons and Profiles**
  Your Anki profile lives in `~/.local/share/Anki2/`. Back it up regularly.
* **Auto‑update AUR package**
  Use a cron or systemd timer to run `yay -Syu --aur --noconfirm`.
* **Flatpak alternative**
  If you face AUR issues, consider Flatpak:

  ```bash
  flatpak install flathub net.ankiweb.Anki
  ```

---

## 6. Further Reading

* ArchWiki: Anki ‹[https://wiki.archlinux.org/title/Anki›](https://wiki.archlinux.org/title/Anki›) ([Arch Wiki][1])
* Anki Manual: Linux Installing ‹[https://docs.ankiweb.net/platform/linux/installing.html›](https://docs.ankiweb.net/platform/linux/installing.html›) ([docs.ankiweb.net][2])
* Snapcraft: Anki on Arch ‹[https://snapcraft.io/install/anki-desktop/arch›](https://snapcraft.io/install/anki-desktop/arch›) ([Snapcraft][3])

Happy memorizing!

[1]: https://wiki.archlinux.org/title/Anki?utm_source=chatgpt.com "Anki - ArchWiki"
[2]: https://docs.ankiweb.net/platform/linux/installing.html?utm_source=chatgpt.com "Installing & Upgrading Anki on Linux - Anki Manual"
[3]: https://snapcraft.io/install/anki-desktop/arch?utm_source=chatgpt.com "Install Anki - Latest on Arch Linux using the Snap Store - Snapcraft"
