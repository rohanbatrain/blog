---
title: "How I Deployed My Hugo Blog on GitHub Pages"
date: 2025-04-26T14:00:00+05:30
description: "A step-by-step guide to deploying a Hugo blog on GitHub Pages, including custom domains."
categories: ["Blogging", "Deployment"]
tags: ["Hugo", "GitHub Pages", "Static Site Deployment", "Custom Domain", "CI/CD", "Web Hosting", "Blog Deployment", "Hugo Build"]
authors:
  - name: "Rohan Batra"
    email: "contact@rohanbatra.in"
    website: "https://rohanbatra.in"
draft: false
# image: "banners/hugo-banner.webp"
aliases:
  - "/en/posts/how-i-deployed-my-hugo-blog-on-github-pages/"
---

## Introduction

In this guide, I'll walk you through the process of deploying a Hugo blog to GitHub Pages, with an optional custom domain (e.g., `blog.rohanbatra.in`). By the end of this guide, you'll have your static Hugo website hosted on GitHub Pages, and you can customize it further as needed.

---

## Prerequisites

Before starting, make sure you have the following:

1. **Git**: Ensure Git is installed on your computer. You can download it [here](https://git-scm.com/downloads).
2. **Hugo**: Install Hugo on your machine. You can follow the instructions on the [official Hugo website](https://gohugo.io/getting-started/installing/).
3. **GitHub Account**: Make sure you have a GitHub account.
4. **Domain Name** (optional): If you want to use a custom domain (e.g., `blog.rohanbatra.in`), have access to your domain registrar's DNS settings.

---

## Step 1: Create a New Hugo Site

If you haven't already created a Hugo site, follow these steps:

1. Open your terminal/command prompt.
2. Run the following command to create a new Hugo site:
   
   ```bash
   hugo new site my-blog
   ```

3. Navigate to the `my-blog` folder:
   
   ```bash
   cd my-blog
   ```

4. Add a theme (you can pick one from the [Hugo themes](https://themes.gohugo.io/)). For example:

   ```bash
   git init
   git submodule add https://github.com/your-theme-repo.git themes/my-theme
   ```

5. Start developing your Hugo blog:

   ```bash
   hugo server
   ```

   Open your browser and go to `http://localhost:1313/` to view your local blog.

---

## Step 2: Set Up GitHub Repository

1. Create a new repository on GitHub:
   - Go to [GitHub](https://github.com) and create a new repository, e.g., `blog`.
   - Do not initialize with a README; we'll do that through Git.

2. Initialize your Hugo site as a Git repository:
   
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   ```

3. Push the code to GitHub:

   ```bash
   git remote add origin https://github.com/username/blog.git
   git push -u origin master
   ```

Replace `username` with your actual GitHub username.

---

## Step 3: Set Up GitHub Pages

1. Go to your GitHub repository and open the **Settings** tab.
2. Scroll down to the **GitHub Pages** section.
3. Under **Source**, select the `gh-pages` branch (or `main`, depending on how you want to deploy).
4. GitHub will provide a URL to access your site (e.g., `https://username.github.io/blog`).

---

## Step 4: Deploying Your Hugo Site to GitHub Pages

To deploy your site, follow these steps:

1. **Build the Hugo Site**:
   - Build your Hugo site with the following command:

     ```bash
     hugo
     ```

   This will generate the static files in the `public/` directory.

2. **Push the `public/` Directory to GitHub Pages**:
   - To deploy your site to GitHub Pages, create a new `gh-pages` branch and push the `public/` folder content to it:

     ```bash
     git checkout --orphan gh-pages
     git reset --hard
     cp -a public/. .
     git add .
     git commit -m "Deploy Hugo site to GitHub Pages"
     git push origin gh-pages --force
     ```

---

## Step 5: Configure Custom Domain (Optional)

If you want to use a custom domain like `blog.rohanbatra.in`, follow these steps:

1. Go to your domain registrar's website (e.g., Namecheap, GoDaddy).
2. Navigate to the **DNS settings** for your domain.
3. Create a **CNAME record** for the subdomain `blog` (or any subdomain you prefer):
   
   - **Name:** `blog`
   - **Type:** `CNAME`
   - **Value:** `username.github.io` (replace `username` with your GitHub username).

4. In your GitHub repository, create a `CNAME` file in the root directory (same level as `index.html`):
   
   ```bash
   echo "blog.rohanbatra.in" > CNAME
   ```

5. Push the `CNAME` file to GitHub:

   ```bash
   git add CNAME
   git commit -m "Add custom domain to GitHub Pages"
   git push origin gh-pages
   ```

6. Finally, go to your GitHub repository’s **Settings** > **Pages** and ensure that the **Custom domain** field has `blog.rohanbatra.in`.

---

## Step 6: Enable HTTPS (Optional)

GitHub Pages supports HTTPS, and you can enable it by following these steps:

1. Go to **Settings** > **Pages** of your repository.
2. Under the **Custom domain** section, enable **Enforce HTTPS**.

Once DNS propagation is complete (can take up to 24 hours), visiting `blog.rohanbatra.in` will serve your Hugo blog over HTTPS.

---

## Conclusion

You’ve successfully deployed your Hugo blog on GitHub Pages with an optional custom domain. Enjoy sharing your content with the world!

---

## Additional Resources

- [Hugo Documentation](https://gohugo.io/documentation/)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)


### How to Use This Documentation:
- Copy and paste this markdown code into your Hugo content file.
- If you're using a specific theme or customization, feel free to tweak the instructions accordingly.
  
