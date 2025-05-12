---
date: 2025-05-12T01:13:12+05:30
title: "How to Set Up Flutter on Arch Linux"
tags: ["flutter", "arch linux", "setup", "mobile development"]
categories: ["Development", "Flutter"]
description: "A complete guide to installing and configuring Flutter on Arch Linux with Android and desktop support."
---

# How to Set Up Flutter on Arch Linux

Setting up Flutter on Arch Linux is straightforward, especially if you're comfortable with the command line. Here's a step-by-step guide to get your development environment up and running with Flutter on Arch.

## 🧰 Prerequisites

Before you start, ensure you have the following:

- A working Arch Linux system (or any Arch-based distro like Manjaro)
- `yay` or any other AUR helper installed

---

## 📦 Step 1: Install Dependencies

```bash
sudo pacman -S --needed base-devel git unzip curl xz
````

These are essential build tools and utilities Flutter depends on.

---

## 🚀 Step 2: Install Flutter via AUR

The easiest way to install Flutter on Arch is through the AUR:

```bash
yay -S flutter
```

This installs the **latest stable** version and sets up the PATH automatically.

---

## 🛠 Optional: Manual Installation

If you prefer cloning manually from the official repository:

```bash
cd ~/development
git clone https://github.com/flutter/flutter.git -b stable
echo 'export PATH="$PATH:$HOME/development/flutter/bin"' >> ~/.bashrc
source ~/.bashrc
```

---

## 📱 Step 3: Install Android Studio

To develop Android apps, you’ll need the Android SDK and Emulator:

```bash
yay -S android-studio
```

After installing:

1. Open Android Studio
2. Go to **SDK Manager** and install:

   * Android SDK
   * Emulator
   * Platform Tools

Then accept all licenses:

```bash
flutter doctor --android-licenses
```

---

## 💻 Step 4: Enable Desktop Support (Optional)

To build for Linux:

```bash
sudo pacman -S gtk3
flutter config --enable-linux-desktop
```

---

## 🧪 Step 5: Run Flutter Doctor

Now verify your setup:

```bash
flutter doctor
```

Fix any issues reported. You might need to install Java, accept SDK licenses, or update environment variables.

---

## 🔧 Step 6: Create a Flutter Project

```bash
flutter create my_app
cd my_app
flutter run
```

You're ready to start building Flutter apps on Arch!

---

## 📝 Summary

| Task            | Command                                       |
| --------------- | --------------------------------------------- |
| Install deps    | `sudo pacman -S base-devel git unzip curl xz` |
| Install Flutter | `yay -S flutter`                              |
| Android Studio  | `yay -S android-studio`                       |
| Accept licenses | `flutter doctor --android-licenses`           |
| Enable desktop  | `flutter config --enable-linux-desktop`       |
| Check setup     | `flutter doctor`                              |

---

Enjoy Flutter development on the fastest Linux distro around 🚀

