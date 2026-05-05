# Shalsabilla Wahyu — Portfolio

A modern, premium portfolio website built with **Nuxt 3** and **Tailwind CSS**.

## ✨ Features
- Monochrome design (black, white, gray only)
- Custom cursor with hover effects
- Smooth scroll reveal animations
- Responsive: desktop, tablet, mobile
- Image carousel with swipe, dots & thumbnails
- Glassmorphism effects
- Cormorant Garamond + DM Sans typography pair
- Vertical timeline for experience
- No progress bars — skill categories with descriptions

---

## 📁 Folder Structure

```
shalsabilla-portfolio/
├── assets/
│   └── css/
│       └── main.css          # Global styles, animations, cursor
├── components/
│   ├── AppNav.vue            # Sticky navigation
│   ├── AppFooter.vue         # Footer
│   ├── HeroSection.vue       # Landing hero
│   ├── AboutSection.vue      # About me + traits
│   ├── ExperienceSection.vue # Vertical timeline
│   ├── SkillsSection.vue     # Skill categories (no bars)
│   ├── ProjectsSection.vue   # Project cards
│   ├── ImageCarousel.vue     # Gallery slider
│   └── ContactSection.vue    # Contact form + links
├── pages/
│   └── index.vue             # Main page
├── nuxt.config.ts
├── tailwind.config.js
└── package.json
```

---

## 🚀 Installation & Running Locally

### Prerequisites
- Node.js 18+
- npm or yarn

### Steps

```bash
# 1. Navigate to project folder
cd shalsabilla-portfolio

# 2. Install dependencies
npm install

# 3. Run development server
npm run dev
```

Visit **http://localhost:3000** in your browser.

### Build for Production

```bash
npm run build
npm run preview
```

### Static Site (for hosting on Netlify/Vercel)

```bash
npm run generate
```

The output will be in the `.output/public` folder.

---

## 🖼️ Adding Your Photo

In `HeroSection.vue`, find the portrait placeholder section and replace the `<div>` placeholder with:

```vue
<img
  src="/your-photo.jpg"
  alt="Shalsabilla Wahyu"
  class="absolute inset-0 w-full h-full object-cover object-center"
/>
```

Place your photo in the `/public` folder.

---

## 🎨 Customization

| File | What to edit |
|------|-------------|
| `HeroSection.vue` | Name, roles, tagline |
| `AboutSection.vue` | Bio, traits, stats |
| `ExperienceSection.vue` | Work experience data |
| `SkillsSection.vue` | Skill categories |
| `ProjectsSection.vue` | Project cards |
| `ImageCarousel.vue` | Gallery slides (replace placeholders with `<img>`) |
| `ContactSection.vue` | Contact links |
| `tailwind.config.js` | Color tokens |
| `assets/css/main.css` | Global styles, cursor |

---

## 🌐 Deployment

**Vercel (recommended):**
1. Push to GitHub
2. Import to Vercel → it auto-detects Nuxt 3
3. Deploy ✓

**Netlify:**
- Build command: `npm run generate`
- Publish directory: `.output/public`

---

Built with ♥ by Shalsabilla Wahyu
