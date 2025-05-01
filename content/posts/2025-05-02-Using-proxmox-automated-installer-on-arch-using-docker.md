---
title: "User Guide: Using the Proxmox Auto Installer Build"
date: 2025-05-02T00:34:02+05:30
draft: false
slug: "proxmox-auto-installer-guide"
tags:
  - proxmox
  - docker
  - automation
  - iso
  - unattended-install
  - virtualization
  - linux
categories:
  - documentation
  - devops
  - infrastructure
description: "Comprehensive guide for generating custom Proxmox VE unattended-install ISOs using Docker and multiple profile-based configurations."
author: "Rohan"
keywords:
  - proxmox
  - docker
  - iso
  - automation
  - unattended install
  - virtualization
toc: true
lastmod: 2025-05-02T00:34:02+05:30
layout: "single"
---

This document describes how to use the Dockerized Proxmox Auto Installer image to generate unattended Proxmox VE installation ISOs for multiple profiles (e.g., `pve-1`, `pve-2`).

---

## Overview

The `proxmox-auto-installer` Docker image wraps the official `proxmox-auto-install-assistant` tool to convert a standard Proxmox VE ISO into an unattended-install ISO using profile-specific `answer.toml` files. By specifying a profile name, you can maintain multiple configurations and generate distinct custom ISOs in a reproducible manner.

---

## Prerequisites

- Docker installed (version 20.10+).  
- A Proxmox VE ISO (e.g., `proxmox-ve_8.4-1.iso`).  
- Profile directories each containing an `answer.toml` file.  
- Write permissions for the output directory.

---

## Directory Structure

```plaintext
Scripts/
├── iso/
│   ├── proxmox-ve_8.4-1.iso       # Base ISO
│   └── output/                    # Generated ISOs
├── secrets/
│   ├── pve-1/
│   │   └── answer.toml            # Profile pve-1 settings
│   └── pve-2/
│       └── answer.toml            # Profile pve-2 settings
├── Dockerfile                     # Build definition
└── entrypoint.sh                  # Profile-aware entrypoint
```

---

## Building the Docker Image

Run the following command from the directory containing the `Dockerfile` and `entrypoint.sh`:

```bash
docker build -t proxmox-auto-installer .
```

- `-t proxmox-auto-installer` tags the image for easy reference.  
- Ensure `entrypoint.sh` has executable permissions (`chmod +x entrypoint.sh`).

---

## Running the ISO Build

### 5.1. Single Profile

To generate an ISO for a single profile (e.g., `pve-1`):

```bash
docker run --rm \
  -v /home/rohan/Documents/Scripts/iso:/iso:ro \
  -v /home/rohan/Documents/Scripts/secrets:/answers:ro \
  -v /home/rohan/Documents/Scripts/iso/output:/out \
  proxmox-auto-installer:latest \
    /iso/proxmox-ve_8.4-1.iso \
    pve-1
```

- **`/iso/...`**: read-only mount of base ISO directory  
- **`/answers/...`**: profile directory mount containing `answer.toml`  
- **`/out/...`**: writeable output directory  

### 5.2. Multiple Profiles

Repeat the command for each profile:

```bash
for profile in pve-1 pve-2; do
  docker run --rm \
    -v $PWD/iso:/iso:ro \
    -v $PWD/secrets:/answers:ro \
    -v $PWD/iso/output:/out \
    proxmox-auto-installer:latest \
    /iso/proxmox-ve_8.4-1.iso $profile
done
```

---

## Generated Output

After each run, you will find:

```plaintext
iso/output/proxmox-ve_8.4-1-auto-pve-1.iso
iso/output/proxmox-ve_8.4-1-auto-pve-2.iso
```

Each ISO is labeled with its profile name.

---

## Troubleshooting

- **Missing answer file**: Ensure `secrets/<profile>/answer.toml` exists and is readable.  
- **Permission denied**: Verify Docker has permissions to read ISO and write output.  
- **`proxmox-auto-install-assistant` errors**: Run interactively to inspect logs.

---

## Cleanup

To remove the Docker image:

```bash
docker rmi proxmox-auto-installer
```

To clear old ISOs:

```bash
rm iso/output/*
```

---

## FAQ

**Q:** Can I use a different ISO version?  
**A:** Yes, replace the ISO filename in the run command.  

**Q:** How do I add a new profile?  
**A:** Create a directory under `secrets/` (e.g., `pve-3/answer.toml`) and rerun.  

**Q:** Can I customize the Dockerfile?  
**A:** Yes, adjust the base image or additional dependencies as needed.  
