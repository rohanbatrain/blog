---
title: "How I Switched from Using GitHub to Netlify"
date: 2025-04-26T16:00:00+05:30
categories: ["Blogging", "Deployment"]
tags: ["Netlify", "GitHub Pages", "CI/CD", "Jenkins"]
draft: false
---

Recently, I decided to switch my blog hosting from **GitHub Pages** to **Netlify**, and here's why.

I had set up GitHub Actions to build my Hugo site and deploy it to the `gh-pages` branch. We don’t use **Jekyll**, and I made sure GitHub Pages was configured to serve the site from the built branch — not using GitHub's default Jekyll build system.

But despite that, something odd kept happening.

Just before the GitHub Action could finish and push the Hugo-built site, GitHub Pages' **default Jekyll builder** would sometimes run automatically — even though we weren’t using it. The result? It would overwrite the `gh-pages` content, and my `index.html` would mysteriously vanish.

I suspect the issue might’ve come from the GitHub Action I had imported — maybe it didn't properly disable Jekyll or triggered an unwanted build.

After a few failed attempts at debugging, I decided to switch to **Netlify**.

And everything just worked. I connected my repo, set the build command to `hugo`, and specified `public/` as the publish directory. That was it. No strange Jekyll interference, no broken deploys, just clean and easy publishing.

If you're running into confusing GitHub Pages behavior, especially with Hugo and CI setups, switching to Netlify might save you a ton of time.