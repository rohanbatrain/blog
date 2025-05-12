---
date: 2025-05-12T00:16:46+05:30
title: "Clone a Private Repo Using GitHub Secrets in GitHub Actions"
description: "A quick guide to securely clone private repositories inside GitHub Actions workflows using secrets."
tags: ["github-actions", "automation", "secrets", "devops", "ci-cd"]
categories: ["GitHub", "CI/CD"]
draft: false
---

# Clone a Private Repo Using GitHub Secrets in GitHub Actions

Cloning a private repository inside another GitHub Actions workflow is a common use case — whether you're reusing shared scripts, configs, or tools. Here’s how to do it securely using GitHub Secrets.

---

## 🔐 Step 1: Generate a Personal Access Token (PAT)

1. Go to **GitHub > Settings > Developer Settings > Tokens**.
2. Click **"Generate new token"** (classic or fine-grained).
3. Grant the following scopes:
   - `repo` for private repos
   - `read:org` if the repo is under an organization
4. Copy the token (you won't see it again).

---

## 🔑 Step 2: Add the Token to Secrets

In your destination repo:

- Go to `Settings > Secrets and variables > Actions`
- Click **"New repository secret"**
- Name it `GH_TOKEN`
- Paste your token

---

## ⚙️ Step 3: Use It in Your Workflow

Here’s an example `yaml` workflow to clone the private repo:

```yaml
name: Clone Private Repo

on:
  workflow_dispatch:

jobs:
  clone:
    runs-on: ubuntu-latest
    steps:
      - name: Enable Git debug logs
        run: |
          echo "GIT_TRACE=1" >> $GITHUB_ENV
          echo "GIT_CURL_VERBOSE=1" >> $GITHUB_ENV

      - name: Checkout current repo
        uses: actions/checkout@v4

      - name: Clone private repo using GH_TOKEN
        run: |
          git clone https://x-access-token:${{ secrets.GH_TOKEN }}@github.com/org-name/private-repo.git

      - name: List cloned contents
        run: ls -la private-repo/
````

---

## 🛡 Tips

* Use **fine-grained tokens** for more security.
* Don’t echo or log the token.
* Ensure the PAT has access to the org and repo.

---

By using GitHub Secrets and PATs, you keep your workflow secure while integrating private code easily.

Need to run scripts or copy files after cloning? Just add steps below!
