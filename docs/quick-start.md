# Quick Start Guide

## Overview

This guide provides quick instructions for working with the MediCal site repository.

## Repository Information

- **Repository**: hsyhhssyy/MediCal-Site
- **Type**: GitHub Pages deployment repository
- **Site URL**: https://medical.hsy.life
- **Content**: Production build of React application

## For Developers

### Viewing the Site

The deployed site can be accessed at:
- **Production**: https://medical.hsy.life
- **GitHub Pages**: https://hsyhhssyy.github.io/MediCal-Site

### Repository Structure

This repository contains **production build files only**:

```
MediCal-Site/
├── index.html          # Main entry point
├── 404.html            # Error page / SPA fallback
├── CNAME               # Custom domain configuration
├── .nojekyll           # Disables Jekyll
├── js/                 # JavaScript bundles
├── css/                # Stylesheets
├── chunk/              # Code-split chunks
└── docs/               # Documentation (this)
```

### Important Notes

⚠️ **This is NOT the source code repository**

- This repository contains only built/compiled files
- Do not edit files directly in this repository
- Changes should be made in the source repository and rebuilt
- Direct changes here will be overwritten on next deployment

## For Maintainers

### Updating the Site

To deploy updates to the site:

1. **Make changes in source repository** (not this one)
2. **Build the project**:
   ```bash
   npm run build
   ```
3. **Deploy to GitHub Pages**:
   ```bash
   # Automated via CI/CD, or manual:
   git push origin HEAD:gh-pages
   ```

### Managing the Domain

The custom domain is configured in the `CNAME` file:

```
medical.hsy.life
```

To change the domain:
1. Update the CNAME file
2. Configure DNS records at your domain provider
3. Wait for DNS propagation (up to 24 hours)

### Branch Strategy

- **gh-pages**: Main branch (production deployment)
- **copilot/read-docs**: Development/feature branches

## For Visitors

### Accessing the Site

Simply visit: https://medical.hsy.life

### Browser Requirements

The site works on:
- ✅ Modern Chrome, Firefox, Safari, Edge
- ✅ Mobile browsers (iOS Safari, Chrome Mobile)
- ⚠️ Internet Explorer 11+ (with reduced features)

### Mobile Experience

The site is optimized for mobile devices:
- Responsive design
- Touch-friendly interface
- Can be added to home screen on iOS/Android

## Common Tasks

### Viewing Documentation

All documentation is in the `docs/` directory:

- **README.md**: Project overview and general information
- **deployment.md**: Deployment and hosting details
- **architecture.md**: Technical architecture and design
- **quick-start.md**: This file

### Checking Deployment Status

After a deployment:

1. **Check GitHub Pages status**:
   - Repository Settings → Pages
   - Look for "Your site is published at..."

2. **Verify site is updated**:
   ```bash
   curl -I https://medical.hsy.life
   ```

3. **Clear cache if needed**:
   - Hard refresh: Ctrl+F5 (Windows) or Cmd+Shift+R (Mac)
   - Or use incognito/private browsing mode

### Troubleshooting

#### Site Not Loading

1. Check if GitHub Pages is down: https://www.githubstatus.com
2. Verify DNS: `dig medical.hsy.life`
3. Check browser console for errors
4. Try accessing via GitHub Pages URL directly

#### Changes Not Appearing

1. Wait 5-10 minutes for GitHub Pages to update
2. Clear browser cache
3. Check if deployment actually succeeded
4. Verify changes were pushed to gh-pages branch

#### SSL Certificate Error

1. Ensure DNS is configured correctly
2. Wait several hours after initial setup
3. Check GitHub Pages settings
4. Enable "Enforce HTTPS" in repository settings

## File Descriptions

### Critical Files

| File | Purpose | Can Edit? |
|------|---------|-----------|
| index.html | Main application entry | ❌ No (will be overwritten) |
| 404.html | Error page / SPA routing | ❌ No (will be overwritten) |
| CNAME | Custom domain config | ✅ Yes (if changing domain) |
| .nojekyll | Disable Jekyll | ✅ Yes (should remain empty) |
| js/*.js | Application code | ❌ No (built files) |
| css/*.css | Stylesheets | ❌ No (built files) |
| chunk/*.js | Code chunks | ❌ No (built files) |
| docs/*.md | Documentation | ✅ Yes (documentation) |

### LICENSE Files

Files ending in `.LICENSE.txt` contain license information for third-party libraries. These should not be removed.

## Development Workflow

If you have access to the source repository:

### 1. Clone Source Repository

```bash
git clone <source-repository-url>
cd <source-repository>
```

### 2. Install Dependencies

```bash
npm install
# or
yarn install
```

### 3. Start Development Server

```bash
npm start
# or
yarn start
```

This will start a local development server, typically at `http://localhost:3000`

### 4. Make Changes

Edit source files in the `src/` directory (not this repository)

### 5. Build for Production

```bash
npm run build
# or
yarn build
```

### 6. Deploy

Build output will be pushed to this (MediCal-Site) repository automatically via CI/CD.

## Resources

### Documentation Links

- **GitHub Pages**: https://docs.github.com/en/pages
- **React**: https://react.dev
- **Custom Domains**: https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site

### Support

For issues or questions:
1. Check documentation in `docs/` directory
2. Review GitHub Issues in the source repository
3. Contact the development team

## License

This project uses several open-source libraries. See `*.LICENSE.txt` files for details.

## Last Updated

This documentation was created on February 12, 2026.

For the most recent information, check the repository's commit history.
