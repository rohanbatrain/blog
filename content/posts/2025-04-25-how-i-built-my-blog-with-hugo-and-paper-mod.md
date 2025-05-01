---
title: "How I Built My Blog"
date: 2025-04-25
categories: ["Blogging"]
authors:
  - name: "Rohan Batra"
    email: "contact@rohanbatra.in"
    website: "https://rohanbatra.in"
draft: false
tags: ["Hugo", "PaperMod", "Static Site Generator", "Web Development", "Blog Setup", "Markdown", "GitHub Pages"]
description: "A behind-the-scenes look at how I built my blog, from setting up Hugo to customizing the PaperMod theme, and everything in between."
image: "banners/hugo-banner.webp"
aliases:
  - "/posts/how-i-built-my-blog-with-hugo-and-paper-mod/"
---



### **Title: How I Built My Blog with Hugo and PaperMod**

Hello there! 👋

Welcome to my digital space where I share my thoughts, creations, and various musings. I thought I’d take a moment to walk you through how I built my blog using **Hugo** — a fast and flexible static site generator — and the **PaperMod** theme, which turned out to be a perfect fit for my needs.

### Why Hugo?

I’ve always been fascinated by the simplicity and speed that static site generators provide. After some research and experimentation, Hugo stood out for its blazing-fast build times, great documentation, and flexible theming system. Unlike traditional CMS platforms, Hugo allows me to focus on writing content without worrying too much about the backend. It’s the perfect solution for someone like me, who wants to keep things minimal and straightforward.

### Setting Up Hugo

To get started, I followed the basic steps of installing Hugo. It’s a straightforward process that doesn’t take much time:

1. **Install Hugo**: I installed Hugo on my machine following the [official installation guide](https://gohugo.io/getting-started/installing/).
2. **Create a new site**: With a simple `hugo new site my-blog`, Hugo created the basic file structure for my site.
3. **Choose a theme**: There are a lot of themes available, but I settled on PaperMod, a minimal, modern theme with a clean design and fantastic features like responsive layouts, syntax highlighting, and built-in search functionality.

### Why PaperMod?

I was immediately drawn to **PaperMod** for its clean, distraction-free design. It has a nice balance of aesthetics and functionality. Here are a few things I love about it:

- **Responsive Design**: The layout adjusts beautifully across devices, so my blog looks good on both desktop and mobile.
- **Minimalistic**: PaperMod’s minimalist design was exactly what I wanted. It provides just the right amount of flair without taking away from the content.
- **Built-in Features**: The theme comes with several useful features out of the box, like support for Google Analytics, Open Graph tags for better social media sharing, and even customizable social media links.

### Configuring the Site

Here’s a quick look at how I set up the config file (`config.toml`), which defines most of the parameters for the blog:

```toml
baseURL = "https://blog.rohanbatra.in/"
title = "Rohan Batra"
paginate = 5
theme = "PaperMod"

enableRobotsTXT = true
buildDrafts = false
buildFuture = false
buildExpired = false

minify:
  disableXML = true
  minifyOutput = true

params:
  env = "production"
  title = "Rohan Batra"
  description = "Rohan Batra's digital space: An eclectic collection of thoughts, creations, and documents of all kinds."
  keywords = ["Blog", "Portfolio", "Thoughts", "Creations", "Documents", "Writing", "Ideas", "Personal"]
  author = "Me"
  DateFormat = "January 2, 2006"
  defaultTheme = "auto" # auto, dark, light
  disableThemeToggle = false

  ShowReadingTime = true
  ShowShareButtons = true
  ShowPostNavLinks = true
  ShowBreadCrumbs = true
  ShowCodeCopyButtons = true
  ShowWordCount = true
  ShowRssButtonInSectionTermList = true
  UseHugoToc = true
  comments = false

  socialIcons:
    - name: x
      url: "https://x.com/"
    - name: stackoverflow
      url: "https://stackoverflow.com"
    - name: github
      url: "https://github.com/"

  analytics:
    google:
      SiteVerificationTag = "XYZabc"
```

As you can see, I’ve customized a few things like enabling Google Analytics, showing the post navigation links, and setting up social media icons. One of my favorite configurations is enabling **showing the reading time** and **code copy buttons** for a more interactive experience.

### Adding Content

With the basic configuration in place, adding content is as simple as creating markdown files in the `content/posts` folder. Hugo supports Markdown out of the box, making it a breeze to write posts. I can even embed code blocks and include syntax highlighting using **highlight.js**, which is automatically enabled in PaperMod.

Here’s an example of a simple post written in markdown:

```markdown
---
title: "My First Blog Post"
date: 2025-04-25
tags: ["Introduction", "Personal"]
---

Welcome to my first post! In this space, I’ll be sharing my thoughts, ideas, and whatever else comes to mind. Stay tuned for more updates.
```

Once the content is written, I simply run `hugo server` to view it locally, and when I’m happy with the results, I deploy it to my server using GitHub Pages or any other hosting platform that supports static sites.

### Customizing and Extending

While **PaperMod** is already feature-packed, Hugo’s flexibility allows me to further extend the site. For instance, I’ve added a **profile mode** that showcases a brief introduction about myself with a link to my posts and tags. You can see it on the homepage, and it adds a nice personal touch.

Another feature I love is the **RSS feed**. With Hugo, you get a built-in RSS feed that is automatically generated for your blog posts. This makes it easy for readers to subscribe to my blog and receive updates.

### Final Thoughts

Building this blog has been an enjoyable process, and I’m really happy with how it turned out. Hugo, combined with the PaperMod theme, provides a simple, fast, and aesthetically pleasing solution for creating a blog without any hassle. Whether you’re a writer, developer, or just someone who wants to share your thoughts, I highly recommend giving it a try.

If you're interested, feel free to browse through my other posts, explore my tags, or suggest changes through the GitHub repository. You can find everything on my [GitHub repo](https://github.com/rohanbatrain/Blog) or reach out through my social media links below.

---

I hope you found this guide helpful. If you’re planning to build your own blog using Hugo and PaperMod, I’d love to hear about your experience!

Happy blogging!
