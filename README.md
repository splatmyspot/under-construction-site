# Under Construction Site

This repository contains a static "Under Construction" page for **splatmyspot.com**. The site features a looping background video, an overlay message, and a logo in the bottom right corner. It is designed for deployment via GitHub and Cloudflare Pages, while large media assets (video and logo) are served from a Cloudflare R2 bucket on a separate subdomain.

---

## Table of Contents

- [Features](#features)
- [Prerequisites](#prerequisites)
- [Local Setup and Testing](#local-setup-and-testing)
- [Deployment](#deployment)
- [Custom Domain Setup](#custom-domain-setup)
- [R2 Integration](#r2-integration)
- [Future Enhancements](#future-enhancements)
- [License](#license)

---

## Features

- **Looping Background Video:** The page displays a full-screen video that loops continuously.
- **Overlay Content:** A compact overlay box near the top displays an "Under Construction" message.
- **Logo Display:** A PNG logo is positioned in the bottom right corner.
- **Separation of Services:** The site is hosted on GitHub/Cloudflare Pages (using a subdomain like `www.splatmyspot.com`), while media assets are served from Cloudflare R2 on a different subdomain (e.g., `assets.splatmyspot.com`).
- **Customizable:** Easily modify the HTML and CSS to adjust the look and feel of your site.

---

## Prerequisites

- Basic knowledge of HTML and CSS.
- [Git](https://git-scm.com/) installed on your computer.
- A modern web browser for testing.
- (Optional) [Python](https://www.python.org/downloads/) installed for running a local test server.

---

## Local Setup and Testing

1. **Clone the Repository:**

   ```sh
   git clone https://github.com/splatmyspot/under-construction-site.git
   cd under-construction-site
Run a Local Server:

If you have Python installed, run a simple HTTP server to test locally.

For Python 3:
sh
Copy
python -m http.server 8000
For Python 2:
sh
Copy
python -m SimpleHTTPServer 8000
Open Your Browser:

Navigate to http://localhost:8000 to see the under construction page in action.

Deployment
This project is set up for deployment via Cloudflare Pages.

Push Your Code to GitHub:

Make sure your repository is up-to-date:

sh
Copy
git add .
git commit -m "Initial commit of under construction page"
git push origin main
Set Up Cloudflare Pages:

Log in to your Cloudflare dashboard.
Navigate to Pages and create a new project.
Connect your GitHub repository to Cloudflare Pages.
Since the site is static (with an index.html in the root), no build command is necessary.
Set your custom domain to the chosen subdomain (e.g., www.splatmyspot.com).
DNS Configuration:

For the GitHub/Pages site, create a CNAME record in Cloudflare DNS:
Name: www
Target: your-project.pages.dev (without any protocol)
(See the Custom Domain Setup section below for more details.)
Custom Domain Setup
Due to conflicts with Cloudflare R2, the apex domain (splatmyspot.com) is currently managed by R2. To resolve this:

For Your GitHub/Pages Site:

Use a subdomain like www.splatmyspot.com for your under construction page.
Add a CNAME record in Cloudflare:
Name: www
Target: your-project.pages.dev (no protocol, no trailing slash)
Redirect the Apex Domain (Optional):

You can set up a page rule or use Cloudflare redirection to forward splatmyspot.com to www.splatmyspot.com.
For R2 Assets:

Bind your R2 bucket to a different subdomain, such as assets.splatmyspot.com.
R2 Integration
If you plan to serve assets (like the background video and logo) from your Cloudflare R2 bucket:

Configure R2:

Log in to Cloudflare and navigate to the R2 section.
Bind your R2 bucket to the subdomain assets.splatmyspot.com.
Update Asset URLs in Your Code:

In your HTML, update the source URLs for the video and logo:

html
Copy
<video class="background-video" autoplay muted loop playsinline>
  <source src="https://assets.splatmyspot.com/your-video.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

<img src="https://assets.splatmyspot.com/logo.png" alt="Logo" class="logo">
Future Enhancements
Additional Formats: Support for additional video formats (e.g., WebM) for better browser compatibility.
Improved Mobile Optimization: Enhance mobile compatibility and optimize load times.
Custom Worker Integration: Consider using a Cloudflare Worker to proxy or manipulate R2 asset responses.
Expanded Content: Add more pages or interactive content as the project evolves.
License
This project is licensed under the MIT License.

Feel free to contribute by opening issues or submitting pull requests.
