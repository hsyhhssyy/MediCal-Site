# Architecture Documentation

## Application Architecture

The MediCal site is a Single Page Application (SPA) built with React and deployed as a static site.

## Frontend Architecture

### Technology Stack

- **UI Framework**: React 
- **Build Tool**: Webpack (inferred from chunk structure)
- **Language**: JavaScript (ES6+)
- **Styling**: CSS

### Application Structure

```
MediCal Application
│
├── Main Bundle (app.js, 76.js)
│   ├── React Core
│   ├── React DOM
│   ├── Router (likely)
│   └── Application Logic
│
├── CSS Bundles
│   ├── app.css (global styles)
│   └── chunk/*.css (component styles)
│
└── Dynamic Chunks
    ├── chunk/117.js
    ├── chunk/231.js
    ├── chunk/250.js
    ├── chunk/316.js
    ├── chunk/382.js
    ├── chunk/70.js
    ├── chunk/852.js
    ├── chunk/870.js
    └── chunk/935.js
```

### Code Splitting Strategy

The application uses code splitting to optimize performance:

1. **Initial Bundle (app.js, 76.js)**
   - Core application code
   - React runtime
   - Essential routing logic

2. **Lazy-Loaded Chunks**
   - Route-specific components
   - Feature modules
   - Loaded on-demand to reduce initial load time

### Routing

As an SPA, the application uses client-side routing:

- **Entry Point**: `index.html`
- **Fallback**: `404.html` (serves as catch-all for client-side routes)
- **History Mode**: Likely uses HTML5 History API
- **Route Handling**: All routes handled by JavaScript router

## Responsive Design

### Mobile Optimization

The application includes mobile-specific optimizations:

```javascript
// From index.html
function f() {
  var e = document.documentElement;
  var w = e.getBoundingClientRect().width;
  var x = 40 * w / 750;
  e.style.fontSize = x >= 40 ? "40px" : x <= 20 ? "20px" : x + "px";
}
```

This function:
- Dynamically adjusts base font size based on viewport width
- Scales from 20px (minimum) to 40px (maximum)
- Reference width: 750px (likely designed for mobile-first)

### Viewport Configuration

```html
<meta name="viewport" content="width=device-width,initial-scale=1,user-scalable=no"/>
```

Features:
- Responsive width matching device
- Initial scale at 1:1
- User scaling disabled (typical for app-like experiences)

### Apple Mobile Web App

```html
<meta name="apple-mobile-web-app-capable" content="yes"/>
<meta name="apple-touch-fullscreen" content="yes"/>
<meta name="apple-mobile-web-app-status-bar-style" content="white"/>
```

Enables:
- Full-screen mode when added to home screen
- Custom status bar styling
- Native app-like experience on iOS

## Performance Optimization

### Bundle Optimization

1. **Code Splitting**
   - Reduces initial bundle size
   - Lazy loads features on demand
   - Improves First Contentful Paint (FCP)

2. **Minification**
   - All JavaScript is minified
   - CSS is optimized
   - Reduces bandwidth usage

3. **Compression**
   - GitHub Pages serves compressed assets
   - Gzip compression enabled by default

### Loading Strategy

1. **Deferred Loading**
   ```html
   <script defer="defer" src="/js/76.js"></script>
   <script defer="defer" src="/js/app.js"></script>
   ```
   - Scripts load after HTML parsing
   - Doesn't block page rendering
   - Executes in order

2. **CSS in Head**
   ```html
   <link href="/css/app.css" rel="stylesheet">
   ```
   - CSS loaded in head for faster rendering
   - Prevents flash of unstyled content (FOUC)

## Browser Compatibility

### IE Compatibility

```html
<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1"/>
```

- Forces latest IE rendering engine
- The `chrome=1` parameter referenced the deprecated Chrome Frame (no longer available since 2014)
- Ensures best compatibility on older IE versions

### Format Detection

```html
<meta name="format-detection" content="telephone=no,address=no"/>
```

- Disables automatic phone number detection
- Disables automatic address detection
- Prevents unwanted auto-linking on mobile devices

## State Management

While not directly visible in the build files, the application likely uses:

- React's built-in state management (useState, useContext)
- Or possibly Redux/MobX for global state
- Local storage for persistence (common in medical apps)

## Data Flow

```
User Interaction
    ↓
React Component
    ↓
State Update
    ↓
Virtual DOM Diff
    ↓
Real DOM Update
```

## Build Process

### Source to Production

1. **Development**
   - Write React components
   - Use modern JavaScript (ES6+)
   - Import CSS/assets

2. **Build**
   - Babel transpiles to browser-compatible JS
   - Webpack bundles and optimizes
   - Code splitting generates chunks
   - Assets are hashed for cache-busting

3. **Output**
   - Static HTML, CSS, JS files
   - Ready for deployment to any static host
   - Optimized for production

## Security Considerations

### Content Security

- All content served over HTTPS (via GitHub Pages)
- Subresource Integrity (SRI) could be added for enhanced security
- No server-side code reduces attack surface

### Data Handling

For a medical application, consider:
- Client-side data encryption
- Secure API communication (if backend exists)
- Session management
- Authentication tokens (if applicable)

## Scalability

### Current Architecture Benefits

1. **Static Hosting**
   - Infinitely scalable via CDN
   - No server-side bottlenecks
   - Low latency worldwide

2. **Code Splitting**
   - Grows gracefully with application size
   - New features don't increase initial load time

3. **Caching**
   - Aggressive caching possible
   - Only changed chunks need re-download

### Future Considerations

If the application grows:
- Consider Service Workers for offline support
- Implement Progressive Web App (PWA) features
- Add backend API for dynamic content
- Implement real-time features if needed

## Dependencies

### Core Libraries

Based on LICENSE files:
- **React**: UI framework
- **React DOM**: React renderer for web
- **Regenerator Runtime**: Async/await support
- **Scheduler**: React's internal scheduler

### Bundle Analysis

To understand exact dependencies, analyze source code or use:
```bash
npm ls                    # List dependencies
webpack-bundle-analyzer  # Visualize bundle composition
```

## Development Workflow

### Typical Workflow

1. **Local Development**
   ```bash
   npm install
   npm start           # Development server
   ```

2. **Building**
   ```bash
   npm run build       # Production build
   ```

3. **Testing**
   ```bash
   npm test           # Run tests
   ```

4. **Deployment**
   - Automatic via CI/CD
   - Or manual push to gh-pages branch

## Monitoring and Analytics

### Recommended Tools

1. **Performance Monitoring**
   - Google Analytics
   - Lighthouse CI
   - Web Vitals tracking

2. **Error Tracking**
   - Sentry
   - LogRocket
   - Rollbar

3. **User Analytics**
   - Google Analytics
   - Mixpanel
   - Amplitude

## Best Practices

### Code Organization

- Component-based architecture
- Separation of concerns
- Reusable UI components
- Centralized state management

### Performance

- Lazy load routes and heavy components
- Optimize images and assets
- Use React.memo for expensive components
- Implement proper loading states

### Accessibility

- Semantic HTML
- ARIA labels where needed
- Keyboard navigation
- Screen reader support

## Future Enhancements

Potential improvements:
- Progressive Web App (PWA) capabilities
- Offline support via Service Workers
- Backend API integration
- Real-time features
- Enhanced analytics
- A/B testing framework
