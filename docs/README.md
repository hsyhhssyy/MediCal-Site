# MediCal Site Documentation

## Overview

MediCal is a medical/healthcare web application deployed as a static site via GitHub Pages. The site is accessible at [medical.hsy.life](http://medical.hsy.life).

## Technology Stack

- **Frontend Framework**: React (production build)
- **Bundler**: Webpack or similar (evidenced by chunked JS files)
- **Hosting**: GitHub Pages
- **Domain**: medical.hsy.life

## Repository Structure

This repository contains the production build of the MediCal application:

```
MediCal-Site/
├── index.html          # Main entry point
├── 404.html            # Custom 404 error page
├── CNAME               # Custom domain configuration
├── .nojekyll           # Disables Jekyll processing for GitHub Pages
├── js/                 # JavaScript bundles
│   ├── app.js          # Main application bundle
│   ├── 76.js           # Additional chunk
│   └── *.LICENSE.txt   # License information for dependencies
├── css/                # Stylesheet bundles
│   └── app.css         # Main application styles
├── chunk/              # Code-split JavaScript chunks
│   └── *.js            # Lazy-loaded modules
└── docs/               # Documentation (this directory)
```

## Features

Based on the build structure, MediCal appears to be:

- **Mobile-Responsive**: Viewport meta tags indicate mobile optimization
- **Single Page Application (SPA)**: Single index.html with React for rendering
- **Code-Split**: Multiple chunks for optimized loading
- **Production-Ready**: Minified and optimized for deployment

## Deployment

### GitHub Pages Configuration

The site is deployed using GitHub Pages with the following configuration:

- **Branch**: `gh-pages` (default)
- **Custom Domain**: `medical.hsy.life` (configured via CNAME)
- **Jekyll**: Disabled (via `.nojekyll` file)

### Deployment Process

This repository receives automated deployments:
1. Source code is built in a CI/CD pipeline
2. Production build artifacts are pushed to the `gh-pages` branch
3. GitHub Pages automatically serves the updated content

## Development

This repository contains only production builds. For development:

1. The source code repository would contain the original React components
2. Development builds would be created using standard React build tools
3. Changes would be built and deployed to this repository

## License Information

The application uses several open-source libraries, including:

- React (MIT License)
- React DOM (MIT License)
- Regenerator Runtime (MIT License)
- Scheduler (MIT License)

Full license information can be found in the `*.LICENSE.txt` files throughout the repository.

## Browser Support

The application includes:
- Mobile viewport optimization
- Apple mobile web app support
- Responsive font sizing (20px to 40px based on viewport width)
- IE Edge compatibility mode

## Maintenance

For site maintenance:

1. **Update Content**: Modify source code and rebuild
2. **Custom Domain**: Update CNAME file if domain changes
3. **Error Pages**: Modify 404.html for custom error handling
4. **Dependencies**: Review LICENSE.txt files when updating libraries

## Support

For issues or questions about the MediCal site, please refer to the main repository or contact the development team.
