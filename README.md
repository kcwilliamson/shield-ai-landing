# Shield AI Landing Page

A modern, animated content protection landing page built with Astro, React, and GSAP. This project demonstrates how to protect digital content from unauthorized AI scraping while educating users about AI training data collection and Cloudflare's content protection solutions.

[![Deployed on Cloudflare Pages](https://img.shields.io/badge/Deployed%20on-Cloudflare%20Pages-F38020?logo=cloudflare&logoColor=white)](https://shield-ai-landing.pages.dev)
[![Built with Astro](https://img.shields.io/badge/Built%20with-Astro-FF5D01?logo=astro&logoColor=white)](https://astro.build)

## 🌐 Live Demo

**Production URL:** https://shield-ai-landing.pages.dev

## 📋 Table of Contents

- [Features](#-features)
- [Tech Stack](#️-tech-stack)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [Development](#-development)
- [Deployment](#-deployment)
- [Content Overview](#-content-overview)
- [Customization](#-customization)
- [Performance](#-performance)
- [Contributing](#-contributing)

## ✨ Features

### Core Features
- **Multi-section Landing Page**: Hero, educational content, protection strategies, resources, and video carousel
- **Advanced GSAP Animations**: Smooth scroll-triggered animations, shape transformations, and parallax effects
- **Interactive Protection Slider**: 4-tier protection level system with detailed product recommendations
- **Video Carousel**: Showcases expert perspectives on AI and content protection
- **Blog Resources Section**: 12 curated Cloudflare blog posts with expandable content
- **Responsive Design**: Mobile-first approach that works seamlessly on all devices
- **Performance Optimized**: Built with Astro for fast load times and optimal SEO

### Technical Features
- **TypeScript**: Full type safety across components and hooks
- **React Hooks**: Custom hooks for animations (`useShapesAnimation`, `useParallaxBars`, `useAntAnimation`)
- **Tailwind CSS**: Utility-first styling with custom gradients and animations
- **Server-Side Rendering**: Astro SSR with Cloudflare adapter
- **Canvas Animations**: Dynamic shape animations using HTML5 Canvas

## 🛠️ Tech Stack

| Technology | Purpose | Version |
|------------|---------|---------|
| **[Astro](https://astro.build)** | Static site framework & SSR | ^4.16.17 |
| **[React](https://react.dev)** | UI components & interactivity | ^18.3.1 |
| **[TypeScript](https://www.typescriptlang.org/)** | Type safety | ^5.6.3 |
| **[GSAP](https://greensock.com/gsap/)** | Animation library | ^3.13.0 |
| **[Tailwind CSS](https://tailwindcss.com)** | Styling framework | ^3.4.14 |
| **[Cloudflare Pages](https://pages.cloudflare.com)** | Hosting & deployment | - |

## 📁 Project Structure

```
shield-ai-landing/
├── src/
│   ├── components/
│   │   └── LandingPage.tsx          # Main landing page component (758 lines)
│   ├── layouts/
│   │   └── Layout.astro             # Base layout wrapper
│   ├── pages/
│   │   └── index.astro              # Entry point
│   ├── hooks/
│   │   ├── useShapesAnimation.ts    # Canvas shape animations
│   │   ├── useParallaxBars.ts       # Parallax effects
│   │   └── useAntAnimation.ts       # Animated ant effects
│   └── globals.css                  # Global styles & Tailwind imports
├── public/                          # Static assets
├── astro.config.mjs                 # Astro + Cloudflare configuration
├── tailwind.config.mjs              # Tailwind customization
├── tsconfig.json                    # TypeScript configuration
├── wrangler.jsonc                   # Cloudflare Workers config
└── package.json                     # Dependencies & scripts
```

## 🚀 Getting Started

### Prerequisites

- **Node.js**: 18.x or higher
- **npm**: 9.x or higher
- **Git**: For version control

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/kcwilliamson/shield-ai-landing.git
   cd shield-ai-landing
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Start development server**
   ```bash
   npm run dev
   ```
   
   The site will be available at `http://localhost:4321`

### Available Scripts

```bash
npm run dev       # Start dev server (http://localhost:4321)
npm run build     # Build for production
npm run preview   # Preview production build locally
npm run astro     # Run Astro CLI commands
```

## 💻 Development

### Development Workflow

1. **Start the dev server**: `npm run dev`
2. **Make changes**: Edit files in `src/`
3. **Hot reload**: Changes appear instantly in the browser
4. **Type checking**: TypeScript validates types on save

### Key Files to Edit

- **Content**: `src/components/LandingPage.tsx` (lines 38-142 for protection configs & blog posts)
- **Styling**: `tailwind.config.mjs` for theme customization
- **Animations**: Custom hooks in `src/hooks/`
- **Layout**: `src/layouts/Layout.astro` for meta tags and SEO

### Custom Hooks

#### `useShapesAnimation()`
Manages canvas-based shape animations with color transformations.
```typescript
const { canvasRef, transformToColorful, transformToGrey } = useShapesAnimation();
```

#### `useParallaxBars()`
Creates parallax scrolling effects for visual elements.

#### `useAntAnimation()`
Animates moving elements along paths.

## 🌐 Deployment

### Cloudflare Pages (Recommended)

This project is optimized for Cloudflare Pages deployment.

#### Option 1: Automatic Deployment (GitHub Integration)

1. Go to [Cloudflare Dashboard](https://dash.cloudflare.com/)
2. Navigate to **Pages** → **Create a project**
3. Connect your GitHub repository
4. Configure build settings:
   - **Build command**: `npm run build`
   - **Build output directory**: `dist`
   - **Framework preset**: Astro
5. Click **Save and Deploy**

#### Option 2: Manual Deployment (Wrangler CLI)

```bash
# Build the project
npm run build

# Deploy using Wrangler
npx wrangler pages deploy dist --project-name=shield-ai-landing
```

### Environment Configuration

No environment variables are required for basic deployment. The project uses:
- **Cloudflare account ID**: Set in `wrangler.jsonc` or via `CLOUDFLARE_ACCOUNT_ID`
- **Production branch**: `main` (default)

### Other Platforms

While optimized for Cloudflare, you can deploy to:
- **Vercel**: Supports Astro with automatic detection
- **Netlify**: Use Astro adapter for Netlify
- **Static hosting**: Build and deploy `dist/` folder anywhere

## 📖 Content Overview

### Sections

1. **Hero Section** (`#hero-section`)
   - Animated text transformation: "It's not Artificial Intelligence" → "It's Collective Intelligence"
   - Canvas-based shape animations with color transitions

2. **Educational Content** (`#section-2`)
   - Explains how AI uses content for training
   - Highlights issues: unauthorized scraping, no compensation, lost monetization

3. **Video Carousel** (`#state-of-ai`)
   - 5 expert perspective videos
   - Smooth horizontal scroll with navigation arrows

4. **Protection Levels** (`#section-4`)
   - Interactive slider with 4 protection tiers:
     - **Level 1**: Open for AI
     - **Level 2**: Selective Access
     - **Level 3**: Controlled
     - **Level 4**: Locked down unless paid
   - Each tier includes products, tips, and summaries

5. **Resources Section** (`#resources-section`)
   - 12 curated blog posts from Cloudflare
   - Expandable "Show More" functionality
   - External links to educational content

### Blog Posts Included

1. Content Signals Policy
2. Good AI Bots Directory
3. AI Insights from Cloudflare Radar
4. Perplexity Case Study
5. People Inc.'s Commentary
6. Content Independence Day
7. AI Index for Customers
8. Choice: Path to AI Sovereignty
9. Per-Customer Bot Defenses
10. Cloudflare Confidence Scorecards
11. Project Galileo AI Protection
12. The Crawl-to-Click Gap

## 🎨 Customization

### Updating Content

#### Protection Levels
Edit the `protectionConfigs` array in `src/components/LandingPage.tsx` (lines 37-65):

```typescript
const protectionConfigs = [
  {
    name: 'Your Level Name',
    summary: 'Description of this protection level',
    products: ['Product 1', 'Product 2'],
    tips: ['Tip 1', 'Tip 2']
  }
];
```

#### Blog Posts
Edit the `blogPosts` array in `src/components/LandingPage.tsx` (lines 69-142):

```typescript
const blogPosts = [
  {
    title: "Post Title",
    url: "https://...",
    author: "Author Name",
    blurb: "Short description"
  }
];
```

### Styling Customization

#### Colors
Modify `tailwind.config.mjs`:

```javascript
module.exports = {
  theme: {
    extend: {
      colors: {
        'brand-orange': '#F6821F',
        'brand-blue': '#0051C3'
      }
    }
  }
}
```

#### Animations
GSAP animation timings can be adjusted in `src/components/LandingPage.tsx`:

```typescript
gsap.to(element, {
  duration: 0.8,  // Adjust timing
  opacity: 1,
  ease: "power2.out"  // Change easing
});
```

## ⚡ Performance

### Lighthouse Scores (Target)
- **Performance**: 90+
- **Accessibility**: 95+
- **Best Practices**: 95+
- **SEO**: 100

### Optimization Features
- Astro's partial hydration (only React components are interactive)
- Lazy loading for images
- Minimal JavaScript bundle
- CSS optimization with Tailwind's JIT compiler
- Cloudflare's global CDN for fast delivery

### Bundle Sizes
- Client JS: ~283 KB (gzipped: ~100 KB)
- Server bundle: ~313 KB
- Total page weight: <500 KB

## 🐛 Troubleshooting

### Common Issues

**Issue**: `npm install` fails with dependency errors
```bash
# Solution: Clear cache and reinstall
rm -rf node_modules package-lock.json
npm install
```

**Issue**: Build fails with TypeScript errors
```bash
# Solution: Check types
npm run astro check
```

**Issue**: GSAP animations not working
- Ensure `gsap` and `gsap/ScrollTrigger` are imported correctly
- Check browser console for errors
- Verify `useEffect` dependencies are correct

**Issue**: Deployment fails on Cloudflare
- Verify `wrangler.jsonc` has correct account ID
- Check build output directory is `dist`
- Ensure `@astrojs/cloudflare` adapter is installed

## 📝 Contributing

This is a private project, but contributions are welcome:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Code Style
- Use TypeScript for all new components
- Follow existing naming conventions
- Add comments for complex logic
- Run type checking before committing

## 📄 License

Private project - All rights reserved

## 🙏 Acknowledgments

- **Cloudflare** for hosting and CDN services
- **Astro team** for the excellent framework
- **GSAP** for powerful animation capabilities
- **Tailwind CSS** for utility-first styling

## 📧 Contact

For questions or feedback about this project:
- **GitHub**: [@kcwilliamson](https://github.com/kcwilliamson)
- **Live Site**: [shield-ai-landing.pages.dev](https://shield-ai-landing.pages.dev)

---

**Built with ❤️ for content creators everywhere**
