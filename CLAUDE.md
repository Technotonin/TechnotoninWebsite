# PAWE — Claude Instructions

## What this project is

PAWE (Portable Affordable Wheelchair Enhancer) is a medical device startup building
a power attachment that converts any manual wheelchair to electric in under 60 seconds.
No tools. No permanent modification. Attaches and detaches by the user independently.

You can read some more information about the device from Technotonin.com

Current stage: seed-funded, pre-FDA-clearance, two beta users, building toward a
$4M raise. The website's primary jobs are: (1) capture waitlist signups from
wheelchair users and caregivers, (2) establish credibility with DME suppliers,
rehab hospitals, and VA centers for LOI outreach, (3) support investor due diligence.

Do not make safety or efficacy claims. Do not reference FDA clearance timelines.
Describe what the product does — not what it will do for someone's health.

---

## Site Structure

<important if="creating or linking any page">
This is a multi-page site. Each page has its own URL and purpose.
Never consolidate everything onto one scrolling page.

Pages:
- `/`               Hero, core value prop, primary waitlist CTA
- `/how-it-works`   Product mechanics, setup steps, technical specs
- `/for-providers`  B2B page for DME suppliers, rehab hospitals, and VA procurement
                    officers. Goal is Letters of Intent. Tone is more formal.
                    Leads with clinical and operational credibility, not user stories.
- `/about`          Mission, founding story, team
- `/waitlist`       Dedicated signup form — minimal distractions

Navigation: persistent top nav on all pages with the PAWE wordmark left,
links center or right, and one accent-colored CTA button ("Join waitlist")
always visible. On mobile this collapses to a hamburger menu.

Never link to external pages without `target="_blank" rel="noopener"`.
Never use `#anchor-links` as a substitute for a real page.
</important>

---

## Brand Identity

### Color Palette

```css
:root {
  /* Primary */
  --color-ink:        #0A0A0A;   /* near-black text */
  --color-paper:      #F5F4F0;   /* warm off-white background */
  --color-accent:     #E8780A;   /* brand orange — CTAs, highlights */
  --color-accent2:    #0099CC;   /* steel blue — secondary actions, data */

  /* Secondary */
  --color-muted:      #6B6B6B;   /* captions, meta text */
  --color-border:     #E0DED8;   /* dividers, outlines */
  --color-surface:    #FFFFFF;   /* cards, modals */

  /* States */
  --color-success:    #16A34A;
  --color-error:      #DC2626;
}
```

### Typography

```html
<!-- In <head> -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Urbanist:wght@400;600;700&display=swap" rel="stylesheet">
```

```css
:root {
  --font-sans: 'Urbanist', system-ui, sans-serif;

  --text-xs:    0.75rem;    /* 12px — legal, captions */
  --text-sm:    0.875rem;   /* 14px — labels, tags, small UI */
  --text-base:  1rem;       /* 16px — body copy */
  --text-lg:    1.125rem;   /* 18px — slightly emphasized body */
  --text-xl:    1.25rem;    /* 20px — subheadings */
  --text-2xl:   1.5rem;     /* 24px — section headings */
  --text-4xl:   2.25rem;    /* 36px — page headings */
  --text-6xl:   3.75rem;    /* 60px — hero headline */
}
```

---

## Tone & Aesthetic

<important if="writing copy or choosing visual style">
**Voice:** Direct, empowering, and human. Write like you're talking to someone capable —
not someone who needs hand-holding. No jargon. No filler. Short sentences that land.
Assume two readers: a 60-year-old wheelchair user and a Series A investor. Both should
feel this was written for them.

**Aesthetic:** Warm precision. Clean structure with human warmth underneath.
Think: purposeful whitespace, confident typography, restrained use of accent color.
Inspired by: Oura, Backbone, Whoop — hardware brands that feel premium and accessible.

**Never mistake minimalism for coldness.** PAWE is about independence and movement.
The design should feel like it's on your side.
</important>

---

## Content Rules

<important if="writing any page copy">
**Headlines:** Lead with the user outcome, not the product feature.
  - Wrong: "Motorized wheelchair attachment"
  - Right: "Your manual chair. Electric in 60 seconds."

**CTAs:** One primary CTA per section. Primary = "Join the waitlist" (accent orange).
Secondary = "Learn how it works" or "See the specs" (ghost button).
Never use "Click here" or "Submit."

**Claims:** No efficacy or safety claims. No comparisons to named competitors.
No promises about FDA clearance timeline. If in doubt, describe the feature
neutrally — what it does, not what it will do for someone's health.

**Numbers:** Always specific. "Under 60 seconds" not "fast." "12 lbs" not "lightweight."
Investors and users both respond to precision.
</important>

---

## Hard Rules

<important if="choosing colors, fonts, or components">
**Never use:**
- `Inter`, `Space Grotesk`, `Roboto` — use Urbanist instead
- Purple, pink, or warm-orange gradients
- Drop shadows heavier than `0 1px 3px rgba(0,0,0,0.08)`
- `border-radius` above `8px` on primary containers (cards, modals, sections)
- Exception: badges, tags, and pills may use up to `20px` for a pill shape
- Stock illustrations or clipart
- Emoji in UI (only in copy if tone demands it)
- `!important` in CSS unless absolutely unavoidable
- Auto-advancing hero carousels
- Accordions above the FAQ section
- Sticky sidebars

**Always use:**
- `Urbanist` for all UI text
- `--color-accent` (#E8780A) for primary CTAs only — one per section maximum
- `--color-accent2` (#0099CC) for secondary actions, data callouts, trust signals
- `--color-paper` (#F5F4F0) as page background — never pure white as the page bg
- Flat photography or clean technical illustration — no stock art, no 3D renders
- `--font-sans` variable for all font-family declarations — never hardcode font names
  in component styles
</important>

---

## Component Priority

<important if="building any new page section">
Reach for the simplest option first. Only add complexity when the content genuinely
requires it.

1. Text + whitespace (default — exhaust this before adding components)
2. Stat callouts (for key numbers: 60s, 10mi, 15lb)
3. Two-column feature rows (text left, visual right or vice versa)
4. Cards (only for comparison or feature lists with 3+ items)
5. Full-width image breaks (max once per page)
</important>

---

## Responsive Design

<important if="writing any CSS or building any component">
Every component must work at three breakpoints:
  - Mobile:   < 768px
  - Tablet:   768px–1024px
  - Desktop:  > 1024px

Mobile-first approach: write base styles for mobile, then use
`@media (min-width: 768px)` and `@media (min-width: 1024px)` to
progressively enhance for larger screens.

Layout rules:
- All multi-column layouts collapse to single column on mobile
- Minimum touch target size: 44×44px (buttons, links, nav items)
- Font sizes never below 16px for body text on any screen size
- No horizontal scrolling at any breakpoint — ever
- Images: always `max-width: 100%` — never fixed pixel widths
- Hero headline: 28–32px on mobile, 48–56px on desktop

Navigation on mobile:
- Hamburger menu (3-line icon) replaces horizontal nav links
- Menu opens as a full-width dropdown, not a sidebar
- Each nav link: minimum 48px tall for touch accessibility
- "Join waitlist" CTA button always visible — never hidden in the menu

Test every component at 375px wide (iPhone SE — the smallest
common screen) before considering it done.
</important>

---

## Accessibility

<important if="building any component or writing any HTML">
- Color contrast: minimum 4.5:1 for body text, 3:1 for large text and UI elements
- All images require descriptive `alt` text — never `alt=""` unless purely decorative
- All interactive elements (buttons, links, inputs) must be keyboard-navigable
- Focus states: never remove `outline` without replacing it with a visible alternative
- Form inputs: always paired with a `<label>` — never rely on placeholder text alone
- Semantic HTML over divs: use `<button>` for buttons, `<a>` for links, never swap them
- ARIA labels on icon-only buttons (e.g. hamburger menu, close button)
- Reading order in HTML must match visual order — no CSS-only reordering of content
</important>

---

## Animations

<important if="adding transitions or motion">
- Default: `transition: all 0.15s ease` for micro-interactions
- Entrance animations: `opacity 0→1` + `translateY(6px)→0`, duration `0.2s`
- Avoid bounce, spin, or elastic easing
- Entrance animations on hero and feature sections only — not on every element
- Never animate content the user hasn't scrolled to yet
- `prefers-reduced-motion`: wrap all animations in:
  ```css
  @media (prefers-reduced-motion: no-preference) { ... }
  ```
- No auto-playing video or looping GIFs without user interaction
</important>

---

## Media

<important if="choosing or placing images">
- Photography: real users in real environments — not staged studio shots
- Never use: stock wheelchair photography, medical imagery, clinical settings
- Aspect ratios: hero images 16:9, feature images 4:3, portraits 1:1
- Alt text: always descriptive and functional, never decorative filler
- No auto-playing video without a visible play button
</important>

---

## Performance

<important if="adding images, scripts, or third-party embeds">
- Images: use `<img loading="lazy">` on everything below the fold
- Hero images: always include `width` and `height` attributes to prevent layout shift
- Scripts: `defer` attribute on all non-critical JS — nothing render-blocking in `<head>`
- Google Fonts already uses `display=swap` — do not add other font sources
- No third-party scripts (analytics, chat widgets, embeds) without explicit instruction
- Inline critical CSS for above-the-fold content if page load becomes an issue
</important>

---

## Footer

<important if="building or editing any page">
Present on all pages. Contains:
- PAWE wordmark (left)
- Nav links: How it works · For providers · About · Waitlist
- Legal: © 2025 Technotonin Industries LLC · Privacy Policy · Terms
- One line of brand voice copy (e.g. "Powering Wheelchairs, Empowering Lives")
- No social media icons until accounts are active
- Background: `--color-ink` (dark), text: `--color-paper` (light)
</important>

---

## File Conventions

- HTML: semantic elements (`<main>`, `<section>`, `<article>`, `<nav>`)
- CSS: custom properties for all brand tokens — no hard-coded hex in component styles
- JS: vanilla first; no framework unless the feature genuinely requires it

---

## Branch Rules

<important if="creating or switching branches">
- `main` — production only; no direct commits
- `dev` — integration branch; merge PRs here first
- Feature branches: `feat/<short-description>` (e.g. `feat/hero-animation`)
- Fix branches: `fix/<short-description>` (e.g. `fix/nav-overflow`)
- Always branch from `dev`, not `main`
- PRs require passing CI before merge to `main`
</important>

## Build Behavior

<important if="building or editing any page">
- Always read PAWE-assets.md before writing any copy or specs
- Build one section at a time — stop and wait for approval before continuing
- Use descriptive image placeholders: <img src="/assets/images/[description].jpg"
  alt="[what this image should show]" width="800" height="450" loading="lazy">
- Never invent testimonials, statistics, or product claims
- After completing each section, list what you built and ask:
  "Ready to continue to the next section?"
- If anything in the brief is ambiguous, ask before building — don't guess
</important>