# Lumina Design Studio Website

A modern, SEO-friendly website for a design studio specializing in custom signage, banners, stickers, and print design services.

## 🚀 Quick Start

```bash
# Install dependencies
npm install

# Start development server
npm run dev

# Build for production
npm run build
```

## 📁 Project Structure

```
studio-website/
├── src/
│   ├── components/      # Reusable components
│   │   ├── Navigation.astro
│   │   └── Footer.astro
│   ├── layouts/         # Page layouts
│   │   └── Layout.astro
│   ├── pages/           # Route pages
│   │   ├── index.astro      # Homepage
│   │   ├── portfolio.astro  # Portfolio
│   │   ├── services.astro   # Services
│   │   ├── about.astro      # About
│   │   └── contact.astro    # Contact
│   ├── styles/          # Global styles
│   │   └── global.css
│   └── content/         # Content data
├── public/              # Static assets
│   ├── favicon.svg
│   └── robots.txt
├── dist/               # Build output
├── astro.config.mjs
└── package.json
```

## 🎨 Features

- **Modern Design**: Clean, professional aesthetic with orange accent color
- **Responsive**: Mobile-first design, works on all devices
- **SEO Optimized**: 
  - Meta tags for each page
  - Open Graph / Twitter Cards
  - Structured data (JSON-LD)
  - Sitemap.xml
  - Robots.txt
- **Fast Performance**: Static HTML generation with Astro
- **Easy Deployment**: Ready for GitHub Pages / Cloudflare Pages

## 📝 Pages

1. **Home** (`/`) - Hero, services preview, featured work, testimonials
2. **Portfolio** (`/portfolio`) - Filterable project gallery
3. **Services** (`/services`) - Detailed service descriptions + pricing
4. **About** (`/about`) - Company story, values, stats
5. **Contact** (`/contact`) - Contact form + information

## 🛠️ Tech Stack

- [Astro](https://astro.build/) - Static site generator
- [Tailwind CSS](https://tailwindcss.com/) - Utility-first CSS
- [@astrojs/sitemap](https://docs.astro.build/en/guides/integrations-guide/sitemap/) - Sitemap generation

## 🚀 Deployment

### GitHub Pages
1. Update `astro.config.mjs` with your actual domain
2. Push to GitHub
3. Enable GitHub Pages in repository settings
4. Set build command: `npm run build`
5. Set publish directory: `dist`

### Cloudflare Pages
1. Connect your GitHub repository
2. Set build command: `npm run build`
3. Set build output directory: `dist`

## 🎨 Customization

### Colors
Edit CSS variables in `src/styles/global.css`:
```css
:root {
  --color-primary: #1a1a1a;
  --color-accent: #ff6b35;
  --color-secondary: #f5f5f5;
}
```

### Content
Update page content in respective `.astro` files in `src/pages/`

### Images
Add actual images to `public/images/` folder and update image paths in components.

## 📧 Contact Form

The contact form currently shows a confirmation message. To make it functional:

1. Use a form service like:
   - [Formspree](https://formspree.io/)
   - [Netlify Forms](https://docs.netlify.com/forms/setup/)
   - [Cloudflare Workers](https://workers.cloudflare.com/)

2. Or connect to your own backend API

## 🔍 SEO Checklist

- [ ] Update site URL in `astro.config.mjs`
- [ ] Update contact email in `src/pages/contact.astro`
- [ ] Add actual portfolio images
- [ ] Update social media links in Footer
- [ ] Add Google Analytics (optional)
- [ ] Submit sitemap to Google Search Console

## 📄 License

MIT

---

Built with ❤️ by Lumina Design Studio
