# Design Guidelines: Instagram Reels Downloader

## Design Approach
**Utility-Focused Application** with visual polish. Following **Material Design** principles adapted for dark mode, with inspiration from modern media platforms like YouTube and Spotify for video-centric UX patterns.

---

## Core Design Elements

### A. Color Palette

**Dark Mode (Primary Theme)**
- Background Primary: `217 33% 10%` (deep slate)
- Background Secondary: `217 33% 15%` (elevated slate)
- Background Tertiary: `217 25% 20%` (card backgrounds)
- Primary Brand: `239 84% 67%` (vibrant indigo - #6366F1)
- Primary Hover: `239 84% 77%` (lighter indigo)
- Accent: `168 76% 42%` (teal for secondary actions)
- Success: `142 71% 45%` (emerald green)
- Error: `0 84% 60%` (red for warnings)
- Text Primary: `0 0% 98%` (near white)
- Text Secondary: `217 10% 65%` (muted gray)
- Border: `217 20% 25%` (subtle dividers)

### B. Typography
**Font Family**: Inter (Google Fonts)
- Hero Headlines: `text-5xl md:text-7xl`, weight 800, tight leading
- Section Headings: `text-3xl md:text-4xl`, weight 700
- Card Titles: `text-xl`, weight 600
- Body Text: `text-base`, weight 400
- Small Text/Meta: `text-sm`, weight 400, text-gray-400
- Button Labels: `text-base`, weight 600

### C. Layout System
**Spacing Primitives**: Tailwind units of `2, 4, 6, 8, 12, 16, 20`
- Container: `max-w-7xl mx-auto px-4`
- Section Padding: `py-16 md:py-20`
- Card Padding: `p-6`
- Element Spacing: `space-y-4` or `gap-4` for grids
- Form Element Spacing: `space-y-3` for tight grouping

### D. Component Library

**Navigation**
- Sticky header: `bg-secondary shadow-xl sticky top-0 z-20`
- Logo with icon, text-2xl font-bold
- Desktop nav: horizontal links with hover:text-primary
- Mobile: hamburger menu icon (collapsible)
- CTA button in nav: `bg-primary px-3 py-1 rounded-full`

**Hero Section**
- Large centered headline with brand color highlight
- Subtitle: max-w-4xl, text-gray-300
- Primary CTA: Input form with rounded-xl container
- Input field: `bg-gray-700 rounded-lg` with focus:ring-primary
- Download button: `bg-primary px-8 py-4 rounded-lg shadow-lg` with hover lift effect

**Cards**
- Background: `bg-secondary rounded-xl`
- Border: `border border-gray-700`
- Hover state: `hover:border-primary transition`
- Shadow: `shadow-2xl` for elevated cards

**Buttons**
- Primary: `bg-primary text-white font-bold rounded-lg` with icon + text layout
- Secondary: `bg-indigo-500` (for AI features)
- Tertiary: `bg-teal-500` (for alternative actions)
- Hover: `translateY(-2px)` with shadow enhancement
- Active: `scale-[0.98]`

**Result/Video Card**
- Two-column layout (md:flex): thumbnail (1/3) + details (2/3)
- Thumbnail: aspect-square, rounded-lg
- Meta info: small text, gray-400
- Action buttons: flex gap-2, full-width on mobile

**Feature Grid**
- Grid: `grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-8`
- Icon: Lucide icons, w-8 h-8, text-primary, centered
- Centered text alignment
- Hover: shadow-primary/50 glow effect

**Loading States**
- Spinner: Rotating circle SVG, text-primary
- Loading text: text-gray-400 below spinner

### E. Icons
**Library**: Lucide Icons (via CDN)
- Navigation: menu, video
- Actions: download, sparkles, scan-text
- Features: zap, graduation-cap, badge-check
- Size: `w-5 h-5` for buttons, `w-8 h-8` for feature cards

---

## Page Structure

**Above the Fold**
- Sticky navigation header
- Hero: Large headline + subtitle + prominent input form
- No hero image (utility-focused, form is the hero)

**Content Sections**
1. How-to-Use: 3-column grid on desktop, numbered steps
2. Features: 4-column grid showcasing benefits
3. FAQ (implied from nav): Accordion-style Q&A
4. Footer: Multi-column with links, social, newsletter

**Result Display**
- Dynamic card revealed after form submission
- Horizontal layout with video preview
- Stacked utility buttons (AI features)
- Gemini output area: collapsible, border-top separation

---

## Interactive Behaviors
- Subtle hover lifts on buttons (`translateY(-2px)`)
- Button press: `active:scale-[0.98]`
- Card borders animate to primary color on hover
- Smooth transitions: `transition duration-150`
- Loading spinners with centered text
- No excessive animations - utility-first approach

---

## Accessibility
- All form inputs have proper labels/placeholders
- Dark mode optimized: minimum contrast ratio 4.5:1
- Focus states: `focus:ring-primary focus:border-primary`
- Icon-text combinations for clarity
- Responsive breakpoints: mobile-first approach

---

## Responsive Strategy
- Mobile: Single column, stacked forms and features
- Tablet (md:): 2-column grids, horizontal input forms
- Desktop (lg:): 3-4 column grids, full navigation
- Container max-width: `max-w-7xl` with responsive padding