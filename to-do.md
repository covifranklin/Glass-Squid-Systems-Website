# Glass Squid Systems — Website To-Do

## Critical (needed before going live)

### Contact form
- Create a free [Formspree](https://formspree.io) account
- Create a new form pointing to `hello@glasssquidsystems.com`
- Replace `YOUR_FORM_ID` in `index.html` (line ~1152) with the ID Formspree gives you
- Add a `<input type="hidden" name="_subject" value="New scoping call request">` inside the form for clean email subjects
- Consider adding a `_next` hidden field to redirect to a thank-you page after submission
- **Alternative:** Use [Cal.com](https://cal.com) or Calendly and replace the email form with a direct booking embed — more useful for a "book a call" CTA than email capture

### Domain & email
- Confirm `glasssquidsystems.com` is registered and DNS is pointing to your host
- Set up `hello@glasssquidsystems.com` (Cloudflare Email Routing → forwards to your Gmail for free, or use Google Workspace)
- Add SPF / DKIM records so outbound email from the domain doesn't land in spam

### Hosting
- Deploy `Website HTML/` as the web root to Netlify, Vercel, or GitHub Pages
  - Netlify: drag-and-drop the `Website HTML/` folder, or connect the GitHub repo and set publish directory to `Website HTML`
  - GitHub Pages: works if `index.html` is at repo root — consider moving files up one level
- Test that `assets/founder-covi.jpg` and `assets/favicon.svg` resolve correctly on the live URL

---

## High priority (UX gaps)

### Footer links — need real URLs
- **LinkedIn:** add your Glass Squid or personal LinkedIn URL
- **Frameworks / Open source / Writing:** either remove these columns until content exists, or add coming-soon pages so links don't dead-end

### Open Graph / social sharing
- Add to `<head>`:
  ```html
  <meta property="og:title" content="Glass Squid Systems — AI systems you can actually rely on"/>
  <meta property="og:description" content="Bespoke AI agent systems designed to be transparent, governable, and built to deliver."/>
  <meta property="og:image" content="https://glasssquidsystems.com/assets/og-image.png"/>
  <meta property="og:url" content="https://glasssquidsystems.com"/>
  <meta name="twitter:card" content="summary_large_image"/>
  ```
- Create an OG image (1200×630px) — the site's hero typography would work well

### Booking flow
- The email capture CTA ("Book a call") is currently a friction point — visitors have to wait for a reply to schedule
- Consider embedding a Cal.com widget directly in the `#contact` section so visitors can self-serve a 30-minute slot

---

## Content

### Missing / placeholder content
- Footer "Lab" section (Frameworks, Open source, Writing) — remove or stub out with real links
- LinkedIn and any other social profiles
- A brief privacy notice or cookie policy if you add analytics (required under UK GDPR for any EU/UK visitors)

### Copy refinements to consider
- Hero subhead: "Transparent, governable, and built to transform your operations" is slightly generic — consider a more concrete claim (e.g. "Every agent scoped. Every decision logged. Every cost capped.")
- The problem/solution section quote is missing a comma: "Most organisations can't integrate AI because they can't trust it . As" — stray space before the period

### Founder photo
- The current photo (`assets/founder-covi.jpg`) works — consider a tighter crop or a version with less background noise for smaller viewports
- Add `width` and `height` attributes to the `<img>` tag to reduce Cumulative Layout Shift

---

## Technical polish

### Performance
- Run the founder photo through [Squoosh](https://squoosh.app) and export as WebP — likely 60–70% smaller
- Add a `<link rel="preload">` for the founder image (it's below the fold but loads eagerly)
- Consider adding `loading="eager"` to the hero section and keeping `lazy` only for below-fold images

### SEO
- Add `<link rel="canonical" href="https://glasssquidsystems.com/"/>` to `<head>`
- Create a `sitemap.xml` (one-pager, so minimal — but still useful for indexing speed)
- Create a `robots.txt` (even a permissive one signals a maintained site)

### Accessibility
- Nav links hidden on mobile (`display:none` via media query) with no hamburger menu — mobile visitors have no navigation. Add a mobile menu or at least keep the "Book a consultation" CTA visible
- Test keyboard navigation through the whole page (tab order, focus states)
- The ambient blobs have `aria-hidden="true"` — good. Check that all decorative SVGs also have `aria-hidden="true"`
- Colour contrast: `var(--muted)` (#6a7775) on cream background — check it passes AA at small sizes

### Analytics
- Add [Plausible](https://plausible.io) (privacy-friendly, GDPR-compliant, no cookie banner needed) or Fathom
- One script tag, no configuration needed for a single-page site

### Tweaks panel
- The dev tweaks panel (`#tweaksPanel`) is hidden in production and harmless — but if you're no longer using it as a design tool, strip it out before final launch to keep the HTML clean (it's ~350 lines of CSS + JS)

---

## Nice to have (post-launch)

- **Case studies page:** one or two worked examples with the "Outcome —" metric shown on the systems cards fleshed out into a full story
- **Writing / Lab section:** tie into your EA Forum or Substack output — this signals credibility to the AI governance audience
- **Structured data:** add `Organization` schema markup so Google can display the business in knowledge panels
- **Print stylesheet:** minimal, but useful if pitch decks link to the site and someone prints it
- **Dark mode:** `prefers-color-scheme: dark` variant — the palette inverts naturally to ink-on-cream → cream-on-ink
