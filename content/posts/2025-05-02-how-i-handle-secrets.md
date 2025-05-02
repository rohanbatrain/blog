---
date: 2025-05-02T21:35:21+05:30
title: "How I Handle Secrets in My DevOps Workflows — A GPG-First Approach to Security"
author: "Rohan Batra"
description: "A detailed look at how I handle secrets securely in my DevOps workflows using GPG encryption, best practices, and automation tools."
tags:
  - security
  - devops
  - gpg
  - encryption
  - automation
  - best practices
categories:
  - security
  - devops
draft: false
slug: "how-i-handle-secrets"
---

# 🔐 How I Handle Secrets in My DevOps Workflows — A GPG-First Approach to Security

As someone who frequently automates deployments and manages infrastructure—across Proxmox clusters, Linux servers, and CI/CD pipelines—I take the handling of secrets seriously. In a world where credentials are often hardcoded into scripts or buried in dotfiles, I wanted a system that was:

- **Tamper-proof**
- **Auditable**
- **Public-repo friendly**
- **Portable across machines**
- And, most importantly, **zero-trust by design**

So I built a secret management system around **GPG-based encryption**, leaning on battle-tested cryptography and deliberate design.

---

## 🧠 The Philosophy: Security by Default, Not by Accident

My guiding principle is simple:  
**No secret should ever exist in plaintext unless it’s actively being used—and only temporarily.**

That means:
- Secrets are always encrypted _before_ being version-controlled.
- Decryption only happens on trusted, controlled environments.
- Private keys are never stored or transmitted insecurely.

---

## 📦 My Toolkit

- 🔐 **GnuPG (GPG)**: Core encryption/decryption engine using ECC (Curve25519)
- 🗂️ **Private GitHub Repositories**: Store only encrypted secrets
- 🧰 **Bash Automation Scripts**: One-liners to encrypt/decrypt with minimal effort
- 🖥️ **Proxmox + Linux VMs**: My playgrounds for infrastructure automation

---

## 🛠️ Implementation Highlights

### 🔑 1. Key Management

I generate a Curve25519-based ECC key pair using GPG:

```bash
gpg --full-generate-key
```

- The **public key** (`.asc`) is safe to distribute—even in public repos.
- The **private key** stays locked down on secure systems (or smartcards/YubiKeys), optionally backed up in offline encrypted storage.

---

### 🧾 2. Encrypting Secrets for Git

All sensitive files (like `.env`, credentials, SSH config) are encrypted before they ever touch version control:

```bash
gpg --encrypt --armor --recipient rohan@example.com secrets.env
```

Only the `.asc` file is committed to git. The original plaintext file is ignored via `.gitignore`.

---

### 🔓 3. Decryption on Trusted Machines

On production or remote environments:
- I import my private key securely:

```bash
gpg --import private.key
```

- Decrypt the file:

```bash
gpg --output secrets.env --decrypt secrets.env.asc
```

Secrets are then passed to applications through environment variables or mounted volumes—never exposed in logs or process lists.

---

## 🔁 Automation with Bash

To avoid human error and manual steps, I use simple automation scripts:

```bash
# encrypt.sh
gpg --encrypt --armor --recipient rohan@example.com "$1"
```

```bash
# decrypt.sh
gpg --output "${1%.asc}" --decrypt "$1"
```

This gives me fast, repeatable, and error-free encryption/decryption anywhere I need it.

---

## 📁 Public GitHub Repos? No Problem

I often build and share automation tools publicly. By encrypting secrets using GPG, I can:
- Keep all sensitive data safe—even in a public repo
- Review encrypted file changes (thanks to ASCII-armored output)
- Stay compliant with audit requirements and zero-leak policies

The method is transparent, but the data is sealed.

---

## 🧠 Lessons Learned

- **Encryption isn’t optional** — it must be the default.
- **Obscurity is not security** — design as if everything is public.
- **Automation ≠ laziness** — it’s how you enforce discipline.
- **Confidence comes from control** — not from hiding how it works.

---

## 🏁 Closing Thoughts

Security, for me, is not a reactive measure—it’s a foundational mindset. Whether I’m deploying infrastructure on Proxmox, managing CI/CD pipelines, or automating remote configuration, I build systems under the assumption that **every repo might become public** and **every system might be probed**.

That’s why I’m not hesitant to share how I handle secrets.  
I follow **established best practices**, such as:
- Encrypting secrets using trusted, open standards (GPG)
- Keeping private keys and passphrases strictly off-record
- Automating workflows without hardcoding sensitive data

I’m well aware of the kinds of **reconnaissance tactics** attackers or auditors use to uncover misconfigurations or credential leaks. In fact, I’ve deliberately designed my approach to withstand that level of scrutiny. I’m sharing this publicly because I’ve already built it with that visibility in mind—and I’m confident in its integrity.

> _"A secure system doesn’t hide how it works. It works securely, even when exposed."_

---

### 📫 Let’s Talk Security

If you’re building infrastructure with security at its core—or want someone who treats it that way—let’s connect. I’m always interested in roles, collaborations, or audits where best practices aren't optional—they're expected.

