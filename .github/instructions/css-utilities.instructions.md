---
description: CSS utility classes and styling practices for this Python/Jinja2 project.
---

# CSS Styling Practices

## Overview
This project uses custom CSS utility classes (similar to Tailwind) defined in `app/static/css/app.css` with a **Harry Potter / Wizarding World** theme. CSS variables in `:root` define the full color palette. Google Fonts "Cinzel Decorative" (headings) and "Crimson Text" (body) are loaded via CDN in `base.html`.

## Theme Variables (`:root`)
```css
--hp-maroon: #740001       /* Gryffindor deep red — primary accent */
--hp-maroon-light: #8B0000
--hp-gold: #D3A625         /* Wizarding gold — highlights, borders */
--hp-gold-light: #EEBA30
--hp-gold-dim: rgba(211,166,37,0.25)
--hp-parchment: #F5E6C8    /* Aged paper — card & page backgrounds */
--hp-parchment-dark: #E8D5B7
--hp-parchment-deep: #D4BC94
--hp-midnight: #0D1B2A     /* Night sky — start screen background */
--hp-navy: #1B2838
--hp-ink: #2B1810          /* Dark brown ink — body text */
--hp-ink-light: #4A3728
--hp-emerald: #1A472A      /* Slytherin green */
```

## Available Utilities

### Layout
```css
.flex, .flex-col, .flex-1
.grid, .grid-cols-5
.items-center, .justify-center, .justify-between
```

### Spacing
```css
/* Padding */
.p-1, .p-3, .p-4, .p-6
.px-3, .px-4, .px-6, .px-8
.py-1\.5, .py-2, .py-3, .py-4
/* Margin */
.mb-2, .mb-3, .mb-4, .mb-6, .mb-8, .mx-auto
/* Gap */
.gap-1, .space-y-2
```

### Sizing
```css
.h-full, .w-full, .w-16, .min-h-full
.max-w-xs, .max-w-sm, .max-w-md
.aspect-square, .overflow-hidden
.min-h-[60px]
```

### Themed Backgrounds
```css
.bg-white           /* maps to --hp-parchment */
.bg-gray-50         /* maps to --hp-parchment */
.bg-gray-100        /* maps to --hp-parchment-dark */
.bg-accent          /* maps to --hp-maroon */
.bg-marked          /* gold dim (marked bingo squares) */
.bg-black/50        /* dark midnight overlay */
.bg-night-sky       /* gradient midnight sky (start screen) */
.bg-parchment       /* layered parchment gradient (game screen) */
.bg-maroon-header   /* gradient maroon (header bar) */
```

### Themed Text
```css
.text-white, .text-gold, .text-parchment, .text-maroon
.text-gray-500 .. .text-gray-900   /* mapped to ink brown tones */
.text-green-600     /* maps to --hp-gold */
.text-green-800     /* maps to --hp-emerald */
.text-amber-500     /* maps to --hp-gold-light */
.text-amber-800, .text-amber-900   /* maps to --hp-maroon */
```

### Typography
```css
.text-xs, .text-sm, .text-lg, .text-3xl, .text-4xl, .text-5xl
.font-semibold, .font-bold
.font-hp-title      /* Cinzel Decorative heading font */
.italic
.text-center, .text-left
.leading-tight
```

### Themed Borders & Shadows
```css
.border, .border-b, .border-2
.border-gray-200, .border-gray-300  /* parchment-deep */
.border-amber-400, .border-marked-border, .border-gold  /* gold */
.rounded, .rounded-lg, .rounded-xl
.shadow-sm, .shadow-xl
.shadow-magic       /* golden glow */
.shadow-magic-lg    /* larger golden glow + depth */
```

### Component Classes
```css
.parchment-card     /* parchment bg + gold border + inner glow */
.board-frame        /* parchment frame for bingo grid with gold border */
.gold-ornament      /* decorative gold line divider with center element */
.stars              /* adds twinkling star pseudo-elements (use on dark bg) */
```

### Bingo Square Styles
```css
.sq-unmarked        /* parchment gradient, ink text, subtle border */
.sq-marked          /* golden glow background, gold border */
.sq-winning         /* bright gold with animated golden-pulse */
.sq-free            /* maroon gradient, gold text, gold border */
```

### Positioning
```css
.fixed, .absolute, .relative
.inset-0
.top-0\.5, .right-0\.5
.z-50
```

### Interactivity
```css
.select-none
.wrap-break-word
.hyphens-auto
```

### Animation
```css
.transition-all, .transition-colors
.duration-150
.animate-magic-appear   /* scale+fade entrance for modals */
.animate-[bounce_0.5s_ease-out]
/* Keyframes: twinkle, golden-pulse, magic-appear, float-sparkle, bounce */
```

## Best Practices

1. **Use CSS variables**: Reference `var(--hp-*)` for all themed colors
2. **Compose utilities**: Combine classes for complex layouts
3. **Use component classes**: `.parchment-card`, `.board-frame`, `.sq-*` for themed elements
4. **Add new utilities to app.css**: Follow existing patterns
5. **Keep specificity low**: Utility classes should be single-purpose

## Example Component Styling
```html
<div class="flex flex-col items-center justify-center min-h-full bg-night-sky stars">
    <div class="parchment-card rounded-xl p-6 max-w-sm">
        <h2 class="font-hp-title font-bold text-gold mb-3">Title</h2>
        <button class="w-full bg-accent text-white font-hp-title py-3 px-6 rounded-lg border-2 border-gold shadow-magic">
            Enter the Great Hall
        </button>
    </div>
</div>
```