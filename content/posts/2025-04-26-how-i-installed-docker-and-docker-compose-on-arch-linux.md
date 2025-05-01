---
title: "How I Installed Docker and Docker Compose on Arch Linux"
date: 2025-04-26T19:00:00+05:30
draft: false
tags: ["arch linux", "docker", "devops", "linux"]
---

# Docker

If you're running Arch Linux and want to get Docker up and running fast — including Docker Compose — here's a clean, one-liner way to do it using the AUR.

## 🛠️ The One-Liner

```bash
sudo pacman -Syu --noconfirm docker && yay -S --noconfirm docker-compose && sudo systemctl enable --now docker && sudo usermod -aG docker $USER
```

This command does the following:
- Updates your system (`pacman -Syu`)
- Installs Docker from the official repos
- Installs Docker Compose from the AUR (via `yay`)
- Enables and starts the Docker service
- Adds your current user to the `docker` group so you can use Docker without `sudo`

## 🔁 Post-Install Tip

After running this, **log out and log back in** to apply the group change.

## ✅ Test It

To verify everything works:

```bash
docker version
docker run hello-world
docker-compose version
```

You should see Docker pull the test image and output a success message.

## 🧠 Why This Matters

Using a one-liner saves time and ensures everything's set up in one shot — perfect for repeatable setups or scripting your dev environment.

Happy containerizing!

