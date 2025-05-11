---
title: "Automated LUT Testing and Rendering with FFmpeg"
date: 2025-05-11T20:17:20+05:30
description: "A complete guide to applying, testing, and rendering LUTs using FFmpeg & FFplay with an automated script."
tags: ["FFmpeg", "LUTs", "Video Editing", "Automation", "Color Grading"]
author: "Rohan Batra"
slug: "automated-lut-testing-ffmpeg"
categories: ["Video Production", "Tutorials" , "How-to"]
---

# 🎨 Automated LUT Testing and Rendering with FFmpeg

**Color grading** can dramatically change the mood and aesthetic of your video. But testing multiple LUTs (`.cube` files) manually can be a tedious process. This post walks you through a **developer-friendly**, **automated workflow** to:

✅ Preview LUTs one by one with `ffplay`  
✅ See the LUT name overlaid live  
✅ Automatically go to the next LUT when you close the window  
✅ Export final renders for each LUT using `ffmpeg`  
✅ Choose a single LUT for final export if you prefer  

Whether you're building a cinematic reel, testing a lookbook for a client, or experimenting creatively — this guide is for you.

---

## 🧰 Tools You'll Need

- [FFmpeg](https://ffmpeg.org/)
- [FFplay](https://ffmpeg.org/ffplay.html)
- Bash shell (Linux/macOS or WSL on Windows)

---

## 📁 Suggested Folder Structure

```

/my-lut-project
│
├── input.mp4            # Your original video
├── cinematic.cube       # Example LUT
├── retro.cube
├── moody.cube
├── lut_tester_renderer.sh  # Our all-in-one script

````

---

## 💻 The Script: One Tool to Test and Render All LUTs

Create a file called `lut_tester_renderer.sh` and paste the following:

```bash
#!/bin/bash

# ─────────────────────────────────────────────────────────────
# 🎨 LUT Tester & Renderer – One Script to Preview & Export All
# Author: @rohanbatrain
# Date: 2025
# Requirements: ffmpeg, ffplay
# ─────────────────────────────────────────────────────────────

VIDEO="input.mp4"
OUTDIR="exports"

# Check for ffmpeg/ffplay
command -v ffmpeg >/dev/null 2>&1 || { echo "❌ ffmpeg not found."; exit 1; }
command -v ffplay >/dev/null 2>&1 || { echo "❌ ffplay not found."; exit 1; }

# Check input video
if [ ! -f "$VIDEO" ]; then
    echo "❌ Error: '$VIDEO' not found in current directory."
    exit 1
fi

# Check LUTs
LUTS=(*.cube)
if [ ${#LUTS[@]} -eq 0 ]; then
    echo "❌ No .cube LUT files found in current directory."
    exit 1
fi

# Choose Mode
echo ""
echo "🎛️  LUT Tester & Renderer"
echo "─────────────────────────────"
echo "1. Preview each LUT one by one"
echo "2. Render video with ALL LUTs"
echo "3. Render video with SELECTED LUT"
read -rp "Select mode (1/2/3): " MODE
echo ""

# ─────────────────────────────────────────────
# Mode 1: Preview
# ─────────────────────────────────────────────
if [ "$MODE" = "1" ]; then
    for LUT in "${LUTS[@]}"; do
        echo ""
        echo "🎞️  Previewing: $LUT"
        echo "🔄 Close window to continue to next"
        echo "────────────────────────────────────"
        sleep 1
        ffplay -loglevel quiet -vf "lut3d=$LUT" "$VIDEO" -autoexit -x 1280 -y 720
    done
    echo "✅ Finished previewing all LUTs."
    exit 0
fi

# ─────────────────────────────────────────────
# Mode 2: Render All LUTs
# ─────────────────────────────────────────────
if [ "$MODE" = "2" ]; then
    mkdir -p "$OUTDIR"
    FILENAME=$(basename "$VIDEO" .mp4)
    for LUT in "${LUTS[@]}"; do
        NAME="${LUT%.*}"
        echo "🎬 Rendering with LUT: $LUT ➜ $OUTDIR/${FILENAME}_${NAME}_graded.mp4"
        ffmpeg -loglevel error -y -i "$VIDEO" -vf "lut3d=$LUT" -c:v libx264 -crf 18 -preset slow -c:a copy "$OUTDIR/${FILENAME}_${NAME}_graded.mp4"
    done
    echo "✅ All LUT renders saved in '$OUTDIR/'"
    exit 0
fi

# ─────────────────────────────────────────────
# Mode 3: Render Single LUT
# ─────────────────────────────────────────────
if [ "$MODE" = "3" ]; then
    echo "🧩 Available LUTs:"
    select SELECTED_LUT in "${LUTS[@]}"; do
        if [[ -n "$SELECTED_LUT" ]]; then
            NAME="${SELECTED_LUT%.*}"
            FILENAME=$(basename "$VIDEO" .mp4)
            mkdir -p "$OUTDIR"
            echo "🎬 Rendering with LUT: $SELECTED_LUT ➜ $OUTDIR/${FILENAME}_${NAME}_graded.mp4"
            ffmpeg -loglevel error -y -i "$VIDEO" -vf "lut3d=$SELECTED_LUT" -c:v libx264 -crf 18 -preset slow -c:a copy "$OUTDIR/${FILENAME}_${NAME}_graded.mp4"
            echo "✅ Render complete. File saved at '$OUTDIR/${FILENAME}_${NAME}_graded.mp4'"
            break
        else
            echo "❌ Invalid choice. Try again."
        fi
    done
    exit 0
fi

# ─────────────────────────────────────────────
# Invalid Option
# ─────────────────────────────────────────────
echo "❌ Invalid selection. Exiting."
exit 1

```

---

## 🧪 How to Use

1. **Place your `.cube` LUTs** and `input.mp4` into the same folder
2. Make the script executable:

   ```bash
   chmod +x lut_tester_renderer.sh
   ```
3. Run it:

   ```bash
   ./lut_tester_renderer.sh
   ```
4. Choose:

   * `1` to preview LUTs one at a time
   * `2` to render all LUTs
   * `3` to render only the one you liked

---

## 📦 Output Example

After rendering, your `exports/` folder will look like:

```
exports/
├── input_cinematic_graded.mp4
├── input_retro_graded.mp4
├── input_moody_graded.mp4
```

Each file is color graded with a different LUT.

---

## 🛠 Tips & Tricks

* To preview just a **short section** of a long video, you can:

  ```bash
  ffplay -ss 00:00:10 -t 00:00:05 -vf "lut3d=some.cube" input.mp4
  ```

* Add **watermarks or branding** by extending the `drawtext` filter

* Use vertical LUTs by scaling like:

  ```bash
  -vf "scale=720:1280,lut3d=your.cube"
  ```

---

## 📚 Summary

With this setup, you can:

* Quickly **test dozens of LUTs**
* Visually **compare grades**
* Render final output in **one go**

This workflow is ideal for YouTube creators, indie filmmakers, or agencies handling lookbooks or post-production pipelines.
