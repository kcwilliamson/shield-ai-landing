# Deployment Guide

This document provides detailed instructions for deploying the Shield AI Landing Page to various platforms.

## 📋 Table of Contents

- [Cloudflare Pages (Recommended)](#cloudflare-pages-recommended)
- [Vercel](#vercel)
- [Netlify](#netlify)
- [Custom Server](#custom-server)
- [Environment Variables](#environment-variables)
- [Troubleshooting](#troubleshooting)

## ☁️ Cloudflare Pages (Recommended)

This project is optimized for Cloudflare Pages with the `@astrojs/cloudflare` adapter.

### Prerequisites
- Cloudflare account
- GitHub repository
- Wrangler CLI (optional, for manual deployment)

### Method 1: Automatic Deployment (GitHub Integration)

This is the easiest method and enables automatic deployments on every push.

#### Steps:

1. **Login to Cloudflare Dashboard**
   - Go to https://dash.cloudflare.com/
   - Navigate to **Pages**

2. **Create New Project**
   - Click **"Create a project"**
   - Select **"Connect to Git"**

3. **Connect GitHub**
   - Authorize Cloudflare to access GitHub
   - Select the `shield-ai-landing` repository

4. **Configure Build Settings**
   ```
   Project name: shield-ai-landing
   Production branch: main
   Build command: npm run build
   Build output directory: dist
   Framework preset: Astro
   ```

5. **Environment Variables** (if needed)
   - None required for basic deployment

6. **Deploy**
   - Click **"Save and Deploy"**
   - Your site will be available at: `https://shield-ai-landing.pages.dev`

#### Automatic Deployments
- Every push to `main` triggers a production deployment
- Preview deployments are created for pull requests
- View deployment history in the Cloudflare dashboard

### Method 2: Manual Deployment (Wrangler CLI)

Use this method for one-off deployments or CI/CD pipelines.

#### Steps:

1. **Install Wrangler**
   ```bash
   npm install -g wrangler
   # or use npx
   ```

2. **Login to Cloudflare**
   ```bash
   wrangler login
   ```

3. **Build the Project**
   ```bash
   npm run build
   ```

4. **Create Pages Project** (first time only)
   ```bash
   npx wrangler pages project create shield-ai-landing --production-branch=main
   ```

5. **Deploy**
   ```bash
   npx wrangler pages deploy dist --project-name=shield-ai-landing
   ```

#### Using Account ID
If you have multiple Cloudflare accounts:
```bash
CLOUDFLARE_ACCOUNT_ID=your_account_id npx wrangler pages deploy dist --project-name=shield-ai-landing
```

### Custom Domain Setup

1. **Add Custom Domain**
   - Go to Pages → Your Project → Custom domains
   - Click **"Set up a custom domain"**
   - Enter your domain (e.g., `shield.example.com`)

2. **Configure DNS**
   - Add CNAME record pointing to `shield-ai-landing.pages.dev`
   - Or let Cloudflare automatically configure (if domain is on Cloudflare)

3. **SSL/TLS**
   - Automatic HTTPS is enabled
   - Universal SSL certificate is provisioned automatically

## ▲ Vercel

### Prerequisites
- Vercel account
- GitHub repository

### Deployment Steps:

1. **Import Project**
   - Go to https://vercel.com/new
   - Click **"Import Git Repository"**
   - Select `shield-ai-landing`

2. **Configure Project**
   ```
   Framework Preset: Astro
   Build Command: npm run build
   Output Directory: dist
   Install Command: npm install
   ```

3. **Change Astro Adapter** (Important!)
   
   Update `astro.config.mjs`:
   ```javascript
   import { defineConfig } from 'astro/config';
   import react from '@astrojs/react';
   import tailwind from '@astrojs/tailwind';
   import vercel from '@astrojs/vercel/serverless'; // Change this

   export default defineConfig({
     output: 'server',
     adapter: vercel(), // Change this
     integrations: [react(), tailwind()],
   });
   ```

   Install Vercel adapter:
   ```bash
   npm install @astrojs/vercel
   ```

4. **Deploy**
   - Click **"Deploy"**
   - Site will be available at `https://your-project.vercel.app`

## 🔷 Netlify

### Prerequisites
- Netlify account
- GitHub repository

### Deployment Steps:

1. **Import Project**
   - Go to https://app.netlify.com/start
   - Connect to GitHub
   - Select `shield-ai-landing`

2. **Configure Build**
   ```
   Build command: npm run build
   Publish directory: dist
   ```

3. **Change Astro Adapter** (Important!)
   
   Update `astro.config.mjs`:
   ```javascript
   import { defineConfig } from 'astro/config';
   import react from '@astrojs/react';
   import tailwind from '@astrojs/tailwind';
   import netlify from '@astrojs/netlify'; // Change this

   export default defineConfig({
     output: 'server',
     adapter: netlify(), // Change this
     integrations: [react(), tailwind()],
   });
   ```

   Install Netlify adapter:
   ```bash
   npm install @astrojs/netlify
   ```

4. **Deploy**
   - Click **"Deploy site"**
   - Site will be available at `https://your-site.netlify.app`

## 🖥️ Custom Server

### Static Build

For static hosting (no server-side rendering):

1. **Update Astro Config**
   
   Change to static output in `astro.config.mjs`:
   ```javascript
   import { defineConfig } from 'astro/config';
   import react from '@astrojs/react';
   import tailwind from '@astrojs/tailwind';

   export default defineConfig({
     output: 'static', // Change to static
     integrations: [react(), tailwind()],
   });
   ```

2. **Build**
   ```bash
   npm run build
   ```

3. **Deploy `dist/` folder**
   - Upload to any static hosting service
   - Examples: AWS S3, GitHub Pages, Apache, Nginx

### Nginx Configuration

```nginx
server {
    listen 80;
    server_name shield-ai.example.com;
    root /var/www/shield-ai-landing/dist;
    index index.html;

    location / {
        try_files $uri $uri/ /index.html;
    }

    # Gzip compression
    gzip on;
    gzip_types text/css application/javascript image/svg+xml;

    # Cache static assets
    location ~* \.(js|css|png|jpg|jpeg|gif|svg|ico|woff|woff2)$ {
        expires 1y;
        add_header Cache-Control "public, immutable";
    }
}
```

## 🔐 Environment Variables

This project doesn't require environment variables for basic deployment. However, if you add features that need them:

### Cloudflare Pages
Add in dashboard: Pages → Settings → Environment variables

### Vercel
Add in: Settings → Environment Variables

### Netlify
Add in: Site settings → Environment variables

## 🐛 Troubleshooting

### Build Fails with "Cannot find module"
```bash
# Solution: Clear node_modules and reinstall
rm -rf node_modules package-lock.json
npm install
```

### Build Succeeds but Site Doesn't Load
- Check adapter configuration matches your platform
- Verify output directory is set to `dist`
- Check browser console for JavaScript errors

### GSAP Animations Not Working
- Ensure build includes client-side JavaScript
- Check that `client:only` directive is used for React components
- Verify GSAP is in `dependencies`, not `devDependencies`

### "Module not found" Errors
```bash
# Ensure all dependencies are installed
npm install

# Check for TypeScript errors
npm run astro check
```

### Cloudflare Pages: "Error: Build failed"
- Check build logs in Cloudflare dashboard
- Verify Node.js version (should be 18+)
- Ensure `@astrojs/cloudflare` is installed

### Performance Issues
- Enable compression (Cloudflare does this automatically)
- Check image sizes and optimize if needed
- Review JavaScript bundle size with build output

## 📊 Monitoring Deployments

### Cloudflare Pages
- **Dashboard**: https://dash.cloudflare.com/
- View deployment history, logs, and analytics
- Monitor performance with Web Analytics

### Deployment Status Badge
Add to README:
```markdown
[![Deployment Status](https://img.shields.io/badge/Deployed%20on-Cloudflare%20Pages-F38020?logo=cloudflare)](https://shield-ai-landing.pages.dev)
```

## 🔄 Rollback

### Cloudflare Pages
1. Go to Pages → Your Project → Deployments
2. Find a previous successful deployment
3. Click "..." → "Rollback to this deployment"

### Vercel
1. Go to Deployments
2. Select previous deployment
3. Click "Promote to Production"

### Netlify
1. Go to Deploys
2. Select previous deploy
3. Click "Publish deploy"

## 📝 CI/CD Integration

### GitHub Actions Example

Create `.github/workflows/deploy.yml`:

```yaml
name: Deploy to Cloudflare Pages

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      
      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: 18
          
      - name: Install dependencies
        run: npm ci
        
      - name: Build
        run: npm run build
        
      - name: Deploy to Cloudflare Pages
        uses: cloudflare/pages-action@v1
        with:
          apiToken: ${{ secrets.CLOUDFLARE_API_TOKEN }}
          accountId: ${{ secrets.CLOUDFLARE_ACCOUNT_ID }}
          projectName: shield-ai-landing
          directory: dist
```

## 📞 Support

For deployment issues:
- Check [Cloudflare Pages docs](https://developers.cloudflare.com/pages/)
- Review [Astro deployment guide](https://docs.astro.build/en/guides/deploy/)
- Open an issue on GitHub

---

**Happy Deploying! 🚀**
