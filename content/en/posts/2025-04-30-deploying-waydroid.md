---
title: "2025 04 30 Waydroid"
date: 2025-04-30T01:17:58+05:30
draft: true
---

# I Spent a Week Trying to Install Waydroid… Here’s How I Finally Got It Working

Installing [Waydroid](https://waydro.id/) — the brilliant project that lets you run full Android in a container on Linux — should be easy. But if you’re not on Ubuntu, expect pain. My week-long journey to get it running on Arch involved broken downloads, MITM spoofing, and some serious headbanging... until I found the one AUR package that fixed everything.

---

## SourceForge 

Waydroid hosts its Android system images on **SourceForge**. While SourceForge is still a functional and appreciated platform, in 2025 it can feel a bit dated — especially since it lacks **download resume support** and can be **painfully slow**, at least in my case.

Maybe it was just me — maybe it was that specific link, that specific mirror, or just bad luck. But living in Dehradun, India, and relying on cellular data, the mirrors were wildly unstable. I tried downloading the `.zip` files multiple times, and each attempt failed partway through. Every time, it restarted from byte zero. No resume, no progress — just endless retries and mounting frustration.

To make matters worse, I tried digging around to find the exact expected locations of the `system` and `vendor` images Waydroid uses internally — but it wasn’t feasible. There's no clear documentation or directory reference for it. Honestly, developers should consider putting that info right on the download page. It would’ve saved a lot of trial, error, and time.

---

## Plan B: Google Colab

Thinking I could outsmart the installer, I used **Google Colab** to download the files. It worked flawlessly — Colab grabbed the `.zip` without choking.

But when I tried moving the files to my system and placing them where Waydroid expected (`/var/cache/waydroid/` or something close), nothing worked. Waydroid uses a custom Python downloader that fetches, verifies, and unpacks the files internally. Dropping in a pre-downloaded file doesn’t cut it — the structure, hash checks, and logic are all tightly integrated. I wasn't just able to find out where to put those images i had them in hand, i was replacing the files which python request library path was creating, as i got that directory when i intentionally disconnected the internet then received an error with the directory on where waydroid is downloading the image, tried replacing those, didn't work for obvious reasons.

---

## Plan C: Spoofing with mitmproxy

At this point, I went full hacker.

I spun up **mitmproxy** to intercept Waydroid’s Python `requests` calls. My idea was simple:
- Spoof the SourceForge URL
- Point it to my local or Colab-hosted file
- Trick the installer

To my surprise, this actually worked. The requests were intercepted and redirected — the file even "downloaded" instantly.

But again, I didn’t know **exactly where to place the file** or how to mimic the post-download structure Waydroid expected. The unpacking logic failed, and I was back to square one.

---

## The Glorious AUR Fix

After nearly giving up, I stumbled across this:

👉 [`waydroid-image-gapps`](https://aur.archlinux.org/packages/waydroid-image-gapps)

Just one command:
```bash
yay -S waydroid-image-gapps
```

And everything worked. This AUR package:
- Downloads the correct Android image with GApps pre-included
- Bypasses the fragile SourceForge download step
- Installs it in the right place with the right structure

No more broken downloads. No more hacking the installer.

---

## Lessons Learned

- If you're on Arch, **check the AUR first**. Someone else has probably already suffered for you.
- SourceForge is still a solid platform, but it’s showing its age for large, non-resumable downloads.
- Waydroid’s internal logic doesn’t like shortcuts.
- Spoofing install scripts with mitmproxy is fun, but fragile.
- Sometimes the right package makes all the difference.
- Clear documentation of required file locations (like `system` and `vendor`) would make the install process far more developer-friendly.

---

## Conclusion

Waydroid is amazing — once it works. But getting there on anything other than Ubuntu can feel like running Android in BIOS mode. If you're on Arch, the `waydroid-image-gapps` AUR package is your lifeline. It saved me after a week of madness, and I hope it saves you too.