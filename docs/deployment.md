# Deployment Guide

## Overview

This document describes the deployment setup and process for the MediCal site.

## Hosting Platform

**GitHub Pages** is used to host the MediCal site, providing:
- Automatic SSL/TLS certificates
- CDN distribution
- High availability
- Zero hosting costs

## Domain Configuration

### Custom Domain Setup

The site uses a custom domain: `medical.hsy.life`

**CNAME Record Setup:**
```
medical.hsy.life → hsyhhssyy.github.io
```

**Repository Configuration:**
- CNAME file contains: `medical.hsy.life`
- GitHub Pages automatically reads this file to configure the domain

### Subdomain vs Apex Domain

This site uses a subdomain (`medical.hsy.life`), which is the recommended approach for GitHub Pages because:
- Subdomains can use CNAME records (more reliable)
- Supports CDN functionality
- Easier SSL certificate management

## Branch Strategy

### gh-pages Branch (Production)

- **Purpose**: Hosts the production build
- **Content**: Compiled, minified, production-ready files
- **Access**: Automatically served by GitHub Pages
- **Protection**: Typically protected to prevent accidental changes

### copilot/read-docs Branch

- **Purpose**: Development/documentation branch
- **Content**: May include additional documentation or development artifacts
- **Deployment**: Not automatically deployed

## Build and Deploy Process

### Typical CI/CD Workflow

1. **Build Stage**
   - Source code is compiled
   - Assets are optimized and minified
   - React app is bundled into static files

2. **Test Stage**
   - Run automated tests
   - Validate build artifacts
   - Check bundle sizes

3. **Deploy Stage**
   - Push build artifacts to `gh-pages` branch
   - GitHub Pages detects changes
   - Site is automatically updated (usually within 1-10 minutes)

### Manual Deployment

If manual deployment is needed:

```bash
# Build the project (in source repository)
npm run build

# Navigate to build output directory
cd dist  # or build/, depending on configuration

# Initialize git if needed
git init
git add .
git commit -m "deploy: update site"

# Push to gh-pages branch
git push -f origin HEAD:gh-pages
```

## File Requirements

### Critical Files

1. **index.html**
   - Entry point for the application
   - Must be present at the root

2. **CNAME**
   - Contains custom domain
   - Required for custom domain to work
   - Must contain only the domain name, no protocol or path

3. **.nojekyll**
   - Prevents GitHub Pages from running Jekyll
   - Required for SPA routing to work correctly
   - Empty file, just needs to exist

4. **404.html**
   - Custom error page
   - Also serves as fallback for SPA routing

## DNS Configuration

### Required DNS Records

For the custom domain to work, the following DNS configuration is required:

```
Type: CNAME
Name: medical
Value: hsyhhssyy.github.io
TTL: 3600 (or automatic)
```

### Verification

To verify DNS is configured correctly:

```bash
# Check CNAME record
dig medical.hsy.life CNAME

# Check if site is accessible
curl -I https://medical.hsy.life
```

## SSL/TLS Certificate

GitHub Pages automatically provides SSL/TLS certificates via Let's Encrypt for custom domains:

- **Initial Setup**: May take several hours after DNS propagation
- **Renewal**: Automatic
- **Force HTTPS**: Can be enabled in repository settings

## Rollback Procedure

To rollback to a previous version:

1. Find the commit hash of the working version:
   ```bash
   git log gh-pages --oneline
   ```

2. Reset to that commit:
   ```bash
   git reset --hard <commit-hash>
   git push -f origin gh-pages
   ```

3. Wait for GitHub Pages to update (1-10 minutes)

## Monitoring

### Site Availability

Check if the site is up:
- Direct access: https://medical.hsy.life
- GitHub status: https://www.githubstatus.com

### Build Status

If using CI/CD:
- Check GitHub Actions or CI platform for build status
- Review deployment logs for errors

## Troubleshooting

### Common Issues

1. **404 on all routes except homepage**
   - Ensure `.nojekyll` file exists
   - Check that 404.html is configured for SPA routing

2. **Custom domain not working**
   - Verify CNAME file content
   - Check DNS propagation: `dig medical.hsy.life`
   - Wait up to 24 hours for DNS changes

3. **SSL certificate error**
   - Ensure DNS is correctly configured
   - Wait several hours after initial setup
   - Check GitHub Pages settings for HTTPS enforcement

4. **Site not updating**
   - Verify push to gh-pages was successful
   - Check GitHub Actions/Pages build status
   - Clear browser cache
   - Wait 10 minutes for propagation

## Security

### Best Practices

1. **Enable HTTPS enforcement** in repository settings
2. **Protect the gh-pages branch** to prevent unauthorized changes
3. **Review dependencies** regularly for security vulnerabilities
4. **Keep build dependencies updated** in the source repository

## Performance

### Optimization

The deployed site includes:
- Minified JavaScript and CSS
- Code splitting for optimal loading
- Compressed assets
- CDN distribution via GitHub Pages

### Monitoring Performance

Use these tools to monitor site performance:
- Google PageSpeed Insights
- WebPageTest
- Chrome DevTools Lighthouse

## Additional Resources

- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [Custom Domain Configuration](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site)
- [Troubleshooting GitHub Pages](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/troubleshooting-jekyll-build-errors-for-github-pages-sites)
