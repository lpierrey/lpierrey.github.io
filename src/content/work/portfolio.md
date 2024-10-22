---
title: Creation of this portfolio
publishDate: 2020-03-02 00:00:00
img: /assets/logo_astro.jpeg
img_alt: Iridescent ripples of a bright blue and pink liquid
description: |
  Short summary of this portfolio's development.
tags:
  - Dev
  - Portfolio
---


<blockquote>
  <span style="font-size: 32px;">Motivations</span>
</blockquote>

In my final year as an engineering student, having an online portfolio has become essential. A website portfolio provides a practical and interactive way to showcase my work to recruiters and peers. In this first blog post, I'll guide you through the process of creating this website, which you can follow as a tutorial.

<blockquote>
  <span style="font-size: 28px;">Technologies</span>
</blockquote>

For this portfolio, we'll use GitHub Pages to host the site and Astro.build as a template provider.

GitHub Pages offers free hosting for any project, with the page linked to your personal or company account. If you already own a custom domain (which can be purchased through DNS providers), you can set it up as your website's URL. However, with the free standard account, you can only host one project at a time.

Astro.build offers a wide range of templates for different purposes, such as portfolios, blogs, and marketing pages.

To avoid redundancy and keep things concise, I'll include links to relevant tutorials for each service as needed.


<blockquote>
  <span style="font-size: 38px;">Starting our project</span>
</blockquote>

Begin by creating a working folder on your local device. This folder will hold all your code and assets.

<blockquote>
  <span style="font-size: 30px;">Selecting a Template and Initiating the Project</span>
</blockquote>


Visit Astro’s website and choose a template that fits your style and industry (make sure to pick a different template from mine, although there's no specific reason for this request).

Once you've found the right template, follow this tutorial to set it up.

Ensure you load the project into the folder you created earlier.

Before proceeding, double-check that the folder contains the Astro template files.


<blockquote>
  <span style="font-size: 30px;">Initializing Your Git Repository</span>
</blockquote>


A GitHub repository is an online directory that stores your project files, which will be used to display your website. Anytime you want to update your site—whether adding a new blog post or updating your career details—these are the files you'll modify.

Start by creating a project on GitHub by following this tutorial.

Your project name must follow the format **.github.io**.

Next, clone your repository:

```
> cd /your_local_project_folder
> git clone https://www.github.com/<USERNAME>/<USERNAME>.github.io.git 
```

This links your local folder to the remote repository.

When done, we must upload our files.

```
> git add * 
> git commit -m "Initial Website Commit"
> git push

```

<blockquote>
  <span style="font-size: 30px;">Setting your Astro template as a GitHub page</span>
</blockquote>

We can deploy our Astro website using GitHub Actions.

1. Copy/Paste and modify this block of code to your astro.config.mjs file.

```
import { defineConfig } from 'astro/config'

export default defineConfig({
  site: 'https://astronaut.github.io',
})
```

This file should be located at the root of your project (in the original folder).

Customize it to fit your website’s URL.

2. Create a new file in your project at .github/workflows/deploy.yml and paste in the YAML below.
Create the folders and the file. Then paste this code: 

```
name: Deploy to GitHub Pages

on:
  # Trigger the workflow every time you push to the `main` branch
  # Using a different branch name? Replace `main` with your branch’s name
  push:
    branches: [ main ]
  # Allows you to run this workflow manually from the Actions tab on GitHub.
  workflow_dispatch:

# Allow this job to clone the repo and create a page deployment
permissions:
  contents: read
  pages: write
  id-token: write

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout your repository using git
        uses: actions/checkout@v3
      - name: Install, build, and upload your site
        uses: withastro/action@v0
        # with:
            # path: . # The root location of your Astro project inside the repository. (optional)
            # node-version: 16 # The specific version of Node that should be used to build your site. Defaults to 16. (optional)
            # package-manager: yarn # The Node package manager that should be used to install dependencies and build your site. Automatically detected based on your lockfile. (optional)

  deploy:
    needs: build
    runs-on: ubuntu-latest
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v1
```

3. On GitHub, go to your repository’s Settings tab and find the Pages section of the settings.

4. Choose GitHub Actions as the Source of your site.

5. Commit the new workflow file and push it to GitHub.

Everything should now be online ! (This was a shameless copy of * [Astro's Tutorial](https://docs.astro.build/en/guides/deploy/github/) and Thibault Ellong Tutorial)