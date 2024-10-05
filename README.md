# How to Set Up a Free CDN using GitHub

This guide will walk you through the process of setting up your own free Content Delivery Network (CDN) using GitHub and popular CDN services. By following these steps, you'll be able to serve your static assets quickly and efficiently without any cost.

## Table of Contents

1. [Introduction](#introduction)
2. [Step 1: Create a GitHub Repository](#step-1-create-a-github-repository)
3. [Step 2: Choose a CDN Service](#step-2-choose-a-cdn-service)
   - [jsDelivr](#jsdelivr) (fast global CDN - npm and GitHub supported)
   - [Statically](#statically) (best for serving images - GitHub, GitLab and Bitbucket supported)
   - [GitHack](#githack) githack (serves github - raw images or HTML files) 
4. [Usage Examples](#usage-examples)
5. [Best Practices](#best-practices)
6. [Troubleshooting](#troubleshooting)

## Introduction

A Content Delivery Network (CDN) is a system of distributed servers that deliver web content to users based on their geographic location. 

## Step 1: Create a GitHub Repository

1. Log in to your GitHub account (or create one if you don't have it).
2. Click on the "+" icon in the top right corner and select "New repository".
3. Name your repository (e.g., "static").
4. Choose to make it public (this is important for the CDN services to access your files).
5. Click "Create repository".

Once created, you can upload your static assets (JS, CSS, images, etc.) to this repository.

## Step 2: Choose a CDN Service

You have three excellent options for free CDN services that work with GitHub repositories:

### jsDelivr

[jsDelivr](https://www.jsdelivr.com/) is a free, opensource CDN that works seamlessly with GitHub.

To use jsDelivr:

1. Upload your file to your GitHub repository.
2. Use the following URL structure to access your file:
   ```
   https://cdn.jsdelivr.net/gh/username/repository@version/file
   ```
   Example: 
   ```
   https://cdn.jsdelivr.net/gh/clashhsalc/static@master/assets/cat.jpg
   ```
   Replace `username` with your GitHub username, `repository` with your repo name, `version` with the tag/branch/commit (use `master` for the latest version), and `file` with the path to your file.

### Statically

[Statically](https://statically.io/) is another free CDN option that works well with GitHub.

To use Statically:

1. Upload your file to your GitHub repository.
2. Use the following URL structure:
   ```
   https://cdn.statically.io/gh/username/repository/branch/file
   ```
   Example:
   ```
   https://cdn.statically.io/gh/clashhsalc/static/master/assets/cat.jpg
   ```
   Replace `username`, `repository`, `branch`, and `file` with your specific details.

### GitHack

[GitHack](https://raw.githack.com/) serves raw files directly from GitHub with proper Content-Type headers. It offers different URLs for production and development use.

To use GitHack:

1. Go to the GitHack website.
2. Paste the raw GitHub URL of your file.
3. GitHack will provide you with two URLs: one for production and one for development.

#### Production URL

Use this URL for live websites and production environments:

- No traffic limits. Files are served via CloudFlare's CDN.
- Files can be automatically optimized by adding `?min=1` to the URL.
- Use a specific tag or commit hash in the URL (not a branch). Files are cached permanently based on the URL. Query string is ignored.

Example:
```
https://raw.githack.com/clashhsalc/static/commit-hash/assets/cat.jpg
https://raw.githack.com/clashhsalc/static/ea45826/assets/cat.jpg
```

#### Development URL

Use this URL for testing and development:

- New changes you push will be reflected within minutes.
- Excessive traffic will be temporarily redirected to corresponding CDN URLs.

Example:
```
https://raw.githack.com/clashhsalc/static/master/assets/cat.jpg
```

Note: Replace `commit-hash` in the production URL with the actual commit hash of your file. For the development URL, you can use the branch name (e.g., `master`).

## Usage Examples

Here's a comparison of how to access the same file (`assets/cat.jpg` in the `static` repository by `clashhsalc`) using each CDN service:

1. jsDelivr:
   ```
   https://cdn.jsdelivr.net/gh/clashhsalc/static@master/assets/cat.jpg
   ```

2. Statically:
   ```
   https://cdn.statically.io/gh/clashhsalc/static/master/assets/cat.jpg
   ```

3. GitHack (Production):
   ```
   https://raw.githack.com/clashhsalc/static/commit-hash/assets/cat.jpg
   ```
   (Replace `commit-hash` with the actual commit hash)

4. GitHack (Development):
   ```
   https://raw.githack.com/clashhsalc/static/master/assets/cat.jpg
   ```

## Best Practices
1. Organize your files in a logical folder structure within your repository.
2. Optimize your assets (minify JS/CSS, compress images) before uploading.
3. Use appropriate file extensions to ensure correct Content-Type headers.
4. Consider using a custom domain with CloudFlare for caching.

## Troubleshooting

- If your files are not updating, make sure you're not using a cached version. Force a refresh.
- Check the CDN service status if its still not working.
  
---

By following this guide, you'll have set up your own free CDN using GitHub. Enjoy faster content delivery!
