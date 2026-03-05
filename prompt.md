# Developer Prompt: Modern Portfolio Website

Create a stunning, responsive portfolio website using **Nuxt 4 (Vue 3)** with static site generation. The portfolio should showcase projects with rich detail, feature smooth animations, and provide an exceptional user experience across all devices.

---

## Tech Stack

| Layer | Technology |
|-------|------------|
| Framework | Nuxt 4 (Vue 3) |
| Language | TypeScript |
| Styling | Vanilla CSS with CSS custom properties |
| Build Output | Static site (`nitro.preset: 'static'`) |
| Icons | Inline SVG |
| Deployment | Netlify-ready with `netlify.toml` |

---

## Design System

### Color Palette

```css
/* Primary - Orange/Red gradient */
--primary-50: #ffeae0;
--primary-100: #ffd1b8;
--primary-500: #ff6a3d;
--primary-600: #ff4b3a;
--primary-700: #e0363a;

/* Accent - Purple */
--accent-purple-500: #8a1eff;
--accent-purple-700: #2b004f;

/* Neutral - Dark theme */
--neutral-50: #fdf7ff;
--neutral-100: #f4e9ff;
--neutral-200: #d9c2ff;
--neutral-300: #a89ac4;
--neutral-600: #5b5270;
--neutral-700: #3c3550;
--neutral-800: #241c38;
--neutral-900: #12051f;
--neutral-950: #05000a;
```

### Spacing Scale

```css
--spacing-xs: 0.5rem;    /* 8px */
--spacing-sm: 1rem;      /* 16px */
--spacing-md: 1.5rem;    /* 24px */
--spacing-lg: 2rem;      /* 32px */
--spacing-xl: 3rem;      /* 48px */
--spacing-2xl: 4rem;     /* 64px */
--spacing-3xl: 6rem;     /* 96px */
```

### Typography

- **Font Family**: System font stack (`-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto...`)
- **Headings**: Bold weight (700-800), tight line-height (1.2)
- **Body**: Normal weight (400), comfortable line-height (1.5-1.7)
- **Hero Title**: `clamp(3.5rem, 8vw, 5.5rem)` with gradient text fill

---

## Page Sections

### 1. Header/Navigation (`components/Header.vue`)

**Features:**
- Fixed position with backdrop blur effect (`backdrop-filter: blur(18px)`)
- Scroll-aware styling (adds shadow and solid background when scrolled)
- Logo/brand name on left
- Center navigation links: About, Projects, Contact
- Right-side CTA buttons: "View projects" (secondary), "Contact me" (primary)
- Mobile hamburger menu with slide-down navigation
- Smooth transitions on all interactions

**Responsive Behavior:**
- Desktop: Full horizontal layout
- Mobile (< 768px): Hamburger menu, vertical nav links, full-width CTAs

---

### 2. Hero Section (`components/Hero.vue`)

**Full viewport height section with:**

**Left Content:**
- Greeting with animated wave emoji (👋) using CSS keyframes
- Large gradient name title
- Role description subtitle
- Brief bio paragraph
- Two CTA buttons: "View My Work" (primary), "Get In Touch" (secondary)
- Stats row: 3 statistics with dividers (e.g., "10+ Projects Delivered", "3+ Years Experience", "100% Client Satisfaction")
- Tech stack badges (8-9 technologies in pill format)

**Right Content (Visual):**
- Hero image with glow effect behind it
- Floating animated badges (2 badges with icons and text)
- Image hover effect (scale + translate)

**Bottom:**
- Scroll indicator with bouncing arrow and "Scroll to explore" text

**Animations:**
- `fade-in-up` staggered entrance for all elements
- `wave` animation on emoji
- `pulse-glow` on background glow
- `float` animation on badges
- `bounce` on scroll arrow

**Responsive:**
- Tablet: Stack to single column, visual moves above content
- Mobile: Simplified layout, smaller typography, hidden scroll indicator

---

### 3. Projects/Features Section (`components/Features.vue`)

**Section Header:**
- Badge label: "Portfolio"
- Section title: "Featured Projects"
- Subtitle description
- Category filter tabs: "All Projects", "E-commerce", "SaaS", "Web Apps", "Landing Pages"
- Each tab shows project count badge

**Project Cards Grid:**
- 3-column grid on desktop, 2 on tablet, 1 on mobile
- Staggered animation on scroll (delay based on index)

**Card Structure:**
- Icon/SVG illustration (40x40, inline SVG)
- Overlay with "Quick View" button (appears on hover)
- Title + year badge
- Tech tags (3-5 tags per project)
- Description paragraph
- Footer with links: "Live Site", "Code" (conditional based on availability)

**Project Modal (Teleport to body):**
- Backdrop with click-to-close
- Large icon + title + meta subtitle
- Full description
- Three detail cards (if available):
  - **The Problem** (with info icon)
  - **Target Audience** (with users icon)
  - **Impact & Solution** (with trend icon)
- Action buttons: "Visit Live Site", "View Source Code"
- Smooth modal enter/exit transitions

**Project Data Structure:**
```typescript
interface Project {
  title: string;
  year: string;
  category: 'E-commerce' | 'SaaS' | 'Web Apps' | 'Landing Pages';
  tags: string[];
  meta?: string;           // Short subtitle
  description: string;
  liveUrl?: string;
  codeUrl?: string;
  problem?: string;
  who?: string;
  impact?: string;
  icon: string;            // Inline SVG string
}
```

---

### 4. Call-to-Action Section (`components/CallToAction.vue`)

**Full-width gradient section:**
- Background: Linear gradient from primary-600 to primary-700
- Decorative circles with low opacity positioned absolutely
- Centered content:
  - Heading: "Let's work together"
  - Subtitle inviting collaboration
  - Two buttons: "Email me" (primary/white), "GitHub" (secondary/outline)

**Responsive:**
- Buttons stack vertically on mobile
- Reduced font sizes

---

### 5. Footer (`components/Footer.vue`)

**Simple footer:**
- Dark background (neutral-900)
- Centered copyright text
- Optional: Extended version with brand info, social links, and navigation columns

---

## Global Styling (app.vue)

**CSS Reset & Base:**
- Universal `box-sizing: border-box`
- Zero margin/padding reset
- `scroll-behavior: smooth` on html/body

**Background:**
- Multi-layer gradient with radial gradients at corners
- Fixed background attachment for parallax-like effect
- Dark color scheme throughout

**Global CSS Variables:**
- All colors and spacing defined in `:root`
- Consistent use of CSS custom properties

---

## Animation Specifications

### Keyframe Animations

```css
/* Entrance fade with upward movement */
@keyframes fade-in-up {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}

/* Scale entrance */
@keyframes fade-in-scale {
  from { opacity: 0; transform: scale(0.95); }
  to { opacity: 1; transform: scale(1); }
}

/* Waving hand */
@keyframes wave {
  0%, 100% { transform: rotate(0deg); }
  10%, 30% { transform: rotate(14deg); }
  20%, 40% { transform: rotate(-8deg); }
  50% { transform: rotate(0deg); }
}

/* Floating elements */
@keyframes float {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-12px); }
}

/* Pulsing glow */
@keyframes pulse-glow {
  0%, 100% { opacity: 0.5; transform: scale(1); }
  50% { opacity: 0.8; transform: scale(1.1); }
}

/* Bouncing scroll indicator */
@keyframes bounce {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(8px); }
}
```

### Animation Timing
- Standard duration: `0.3s` - `0.6s`
- Easing: `cubic-bezier(0.4, 0, 0.2, 1)` (ease-out) or `ease`/`ease-out`
- Stagger delays: `0.1s` increments
- Hover transitions: `0.2s` - `0.3s`

---

## Responsive Breakpoints

| Breakpoint | Max Width | Key Changes |
|------------|-----------|-------------|
| Desktop | > 1024px | Full 3-column grid, side-by-side hero |
| Tablet | 1024px | 2-column grid, stacked hero |
| Mobile | 768px | Single column, hamburger menu, simplified |
| Small Mobile | 480px | Compact spacing, smaller text |

---

## File Structure

```
portfolio/
├── app.vue                    # Root with global styles
├── nuxt.config.ts             # Nuxt config (static preset)
├── netlify.toml               # Deployment config
├── pages/
│   └── index.vue              # Home page assembling sections
├── components/
│   ├── Header.vue             # Fixed navigation
│   ├── Hero.vue               # Hero section
│   ├── Features.vue           # Projects showcase
│   ├── CallToAction.vue       # Contact CTA
│   └── Footer.vue             # Footer
├── public/                    # Static assets
└── README.md                  # Project documentation
```

---

## Performance Guidelines

1. **Static Generation**: Use `nuxt generate` for pre-rendered HTML
2. **Lazy Loading**: Use `useLazyFetch` for non-blocking data
3. **CSS Optimization**: Scoped styles in components, no unused CSS
4. **Image Optimization**: Use Cloudinary or similar CDN for images
5. **Font Loading**: Use system font stack (no external font requests)

---

## Accessibility Requirements

1. **Semantic HTML**: Proper heading hierarchy, section landmarks
2. **Keyboard Navigation**: All interactive elements focusable
3. **ARIA Labels**: Menu toggle with `aria-label` and `aria-expanded`
4. **Color Contrast**: Ensure 4.5:1 ratio for text
5. **Focus States**: Visible focus indicators on all interactive elements
6. **Reduced Motion**: Respect `prefers-reduced-motion` media query

---

## Deployment Configuration (netlify.toml)

```toml
[build]
  command = "npm run generate"
  publish = ".output/public"

[[redirects]]
  from = "/*"
  to = "/200.html"
  status = 200
```

---

## Content Guidelines

### Project Categories
- **E-commerce**: Online stores, marketplaces, shopping platforms
- **SaaS**: Subscription-based software, dashboards, tools
- **Web Apps**: Interactive applications, utilities, platforms
- **Landing Pages**: Marketing sites, promotional pages

### Writing Style
- Professional yet approachable tone
- Focus on problem → solution → impact narrative
- Quantify achievements where possible ("40% reduction", "100+ users")
- Use active voice
- Keep descriptions concise but informative (2-3 sentences)

---

## Deliverables Checklist

- [ ] Responsive header with mobile menu
- [ ] Animated hero section with stats and tech stack
- [ ] Projects grid with category filtering
- [ ] Project detail modals with rich information
- [ ] Call-to-action section with contact links
- [ ] Footer with copyright
- [ ] Smooth scroll navigation
- [ ] All hover/focus states styled
- [ ] Mobile-responsive at all breakpoints
- [ ] Static generation configured
- [ ] Deployment-ready with netlify.toml

---

## Example Commands

```bash
# Install dependencies
npm install

# Development server
npm run dev

# Build for production
npm run generate

# Preview production build
npm run preview
```

---

## Success Criteria

The portfolio should:
1. **Load instantly** (pre-rendered static HTML)
2. **Feel premium** through smooth animations and micro-interactions
3. **Work perfectly** on all device sizes
4. **Tell a story** about the developer's skills and experience
5. **Convert visitors** into contacts through clear CTAs
6. **Showcase projects** with enough detail to demonstrate expertise
