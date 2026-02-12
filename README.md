# MediCal Site

A medical/healthcare web application built with React and deployed via GitHub Pages.

🌐 **Live Site**: [medical.hsy.life](https://medical.hsy.life)

## Overview

This repository contains the production deployment of the MediCal web application. The site is a single-page application (SPA) built with React and optimized for both desktop and mobile devices.

## 📚 Documentation

Comprehensive documentation is available in the [`docs/`](./docs/) directory:

- **[Project Overview](./docs/README.md)** - General information about the project
- **[Quick Start Guide](./docs/quick-start.md)** - Getting started and common tasks
- **[Deployment Guide](./docs/deployment.md)** - Deployment process and configuration
- **[Architecture](./docs/architecture.md)** - Technical architecture and design decisions

## 🚀 Quick Links

- **Production Site**: https://medical.hsy.life
- **GitHub Pages URL**: https://hsyhhssyy.github.io/MediCal-Site
- **Repository**: https://github.com/hsyhhssyy/MediCal-Site

## 📋 About This Repository

**Important**: This is a **deployment repository** containing only production build files.

- ✅ Contains: Compiled, minified, production-ready files
- ❌ Does not contain: Source code, development files, or build configuration
- 🔄 Updates: Automatically deployed from source repository

### Repository Contents

```
MediCal-Site/
├── index.html          # Application entry point
├── 404.html            # Error page / SPA routing fallback
├── CNAME               # Custom domain: medical.hsy.life
├── .nojekyll           # GitHub Pages configuration
├── js/                 # JavaScript bundles
├── css/                # Stylesheets
├── chunk/              # Code-split modules
├── docs/               # Documentation
└── README.md           # This file
```

## 🛠️ Technology Stack

- **Frontend**: React
- **Build Tool**: Webpack
- **Hosting**: GitHub Pages
- **Domain**: medical.hsy.life
- **CDN**: GitHub's global CDN

## 📱 Features

- **Responsive Design**: Optimized for mobile and desktop
- **Progressive Loading**: Code-splitting for optimal performance
- **Mobile-First**: Designed for touch devices
- **Fast & Secure**: Served via HTTPS with global CDN

## 🔧 For Developers

### Viewing the Site Locally

Since this is a static site, you can serve it locally:

```bash
# Using Python
python -m http.server 8000

# Using Node.js
npx http-server

# Using PHP
php -S localhost:8000
```

Then visit `http://localhost:8000`

### Making Changes

⚠️ **Do not edit files directly in this repository**

Changes should be made in the source repository and deployed through the build process. Direct edits here will be overwritten on the next deployment.

## 📦 Deployment

This repository is automatically updated when:

1. Changes are made in the source repository
2. A production build is created
3. Build artifacts are pushed to the `gh-pages` branch
4. GitHub Pages deploys the updates (typically within 1-10 minutes)

For more details, see the [Deployment Guide](./docs/deployment.md).

## 🌍 Custom Domain

The site is served from the custom domain `medical.hsy.life`, configured via:

- **CNAME file**: Contains the domain name
- **DNS Configuration**: CNAME record pointing to GitHub Pages
- **SSL/TLS**: Automatically provided by GitHub Pages

## 📄 License

This project uses several open-source libraries. License information can be found in:

- `js/*.LICENSE.txt` - JavaScript library licenses
- `chunk/*.LICENSE.txt` - Additional dependency licenses

Core dependencies include:
- React (MIT License)
- React DOM (MIT License)
- Other supporting libraries (see LICENSE.txt files)

## 🤝 Contributing

As this is a deployment repository, contributions should be made to the source repository. This repository only receives automated deployments.

## 📞 Support

For questions or issues:

1. Review the [documentation](./docs/)
2. Check for known issues in the source repository
3. Contact the development team

## 📊 Repository Statistics

- **Type**: Static site deployment
- **Branch**: gh-pages (production)
- **Updates**: Automated via CI/CD
- **Hosting**: GitHub Pages

## 🔍 Additional Information

For detailed technical information, please refer to:

- **Architecture details**: See [architecture.md](./docs/architecture.md)
- **Deployment procedures**: See [deployment.md](./docs/deployment.md)
- **Quick reference**: See [quick-start.md](./docs/quick-start.md)

---

**Last Updated**: February 2026

For the latest changes, check the [commit history](https://github.com/hsyhhssyy/MediCal-Site/commits/gh-pages).
