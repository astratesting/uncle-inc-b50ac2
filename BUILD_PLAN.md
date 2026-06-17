# Uncle Inc. — Build Plan

## 1. PRODUCT
A Next.js 14 App Router marketing landing page for **Uncle Inc.**, an AI-assisted MVP development platform aimed at non-technical first-time founders. The site has one job: convert qualified visitors into a "Join Waitlist" email capture. The hero pitch — *Validate Your Startup Idea Before You Build It* — directly addresses the ICP's core pain (building something nobody wants) and frames Uncle as a structured validation+build pipeline rather than another no-code toy. Research confirms a saturated solo-freelancer invoice-dunning category and a parallel underserved segment of pre-PMF founders who over-invest in code; the page is built to position Uncle as the disciplined alternative to "just launch and pray."

## 2. WHO IT'S FOR
**Primary ICP:** Non-technical, first-time, pre-PMF startup founders, solo or in tiny teams, aged ~25–45, who have a hypothesis and a weekend of momentum but no validation discipline. They are time-poor, skeptical of fluff, allergic to fake social proof, and decide in 10 seconds whether to scroll or stop. They respond to:
- Concrete, jargon-light language ("validate before you build," not "synergize your go-to-market").
- Visible structure (named sections, real feature names, real prices).
- Honesty — empty counters and invented logos would actively repel this persona.

**Design implications:** oversized type that reads in 3 seconds, one primary CTA repeating across the page, no carousel, no popups, no chat widget, real prices listed, FAQ that answers objections directly.

## 3. LOOK & FEEL

**Visual system:**
- **Vibe:** Bold Frontier. Confident, opinionated, dark, slightly punk. Sharp 0px border-radius on cards, buttons, and inputs. No drop shadows, no glassmorphism, no gradients except a single magenta→flame accent used sparingly on the CTA section.
- **Palette (Tailwind `brand`):** `ink #0a0a0f` (page bg), `flame #ff6b35` (primary CTA, accents), `magenta #e91e8c` (highlight, gradient partner), `acid #b8ff3a` (secondary accent, "popular" tag, check icons), `white #ffffff` (body text), `ink-2 #14141b` (card bg), `ink-3 #1c1c26` (elevated surface / nav).
- **Typography:** Body = Inter (Google Fonts, variable). Headlines = **Archivo Black** (Google Fonts) — chunky, geometric, oversized. Tailwind families: `font-sans` (Inter) and `font-display` (Archivo Black). Hero headline clamps ~56px → 112px across breakpoints; section H2s ~40px → 64px; body 16–18px.
- **Spacing/layout:** Max content width 1200px, generous vertical rhythm — each section is `py-24 md:py-32`. 12-col grid feel via simple flex/grids; cards use `gap-6`.
- **Iconography:** Inline SVG, 1.5px stroke, 24px default. No icon library dependency. Each feature gets a custom 2-color glyph (flame + acid) on a `ink-3` square with sharp corners.
- **Imagery:** None. Pure type, color blocks, and iconography — this is honest, fast, and on-brand for a pre-launch product.
- **Motion:** Reduced. CSS-only fade-in on hero text via `animation-delay` (no framer-motion dep). Smooth scroll globally. Buttons get a 1-frame invert on hover (acid bg / ink text). Accordion uses `<details>` for zero-JS expand/collapse.

**Screens (sections), top to bottom:**

1. **Nav (`components/Nav.tsx`)** — Sticky, `bg-ink-3/90 backdrop-blur`, `border-b border-white/5`. Left: "Uncle Inc." wordmark in `font-display` with a small flame-orange square dot. Center: `Features`, `Pricing`, `FAQ` as anchor links. Right: `Join Waitlist` button (flame bg, ink text, sharp). On scroll past 64px, nav adds a subtle bottom border glow.

2. **Hero (`components/Hero.tsx`)** — Full-width `min-h-[88vh]`, `bg-ink`. Top-left tiny tag: "PRE-LAUNCH · 2026" in acid. Centered headline (Archivo Black): "Validate Your Startup Idea Before You Build It" with the word "Validate" underlined in flame via a hand-drawn-feel SVG stroke. Subtext (Inter, 20px, `text-white/70`, max-w-2xl): "Uncle is an AI-assisted platform that helps non-technical founders go from idea to validated MVP in days, not months — no code required." Two buttons: primary flame "Join Waitlist" (scrolls to #waitlist), secondary outline "See How It Works" (scrolls to #features). No stats row. A small `text-white/40` line: "Currently in private beta."

3. **Features (`components/Features.tsx`)** — `id="features"`, `bg-ink`, `py-32`. Eyebrow "WHAT YOU GET" (acid, uppercase, tracked), H2 "Everything you need. Nothing you don't." 3×2 grid of cards on `md:grid-cols-3`, single column on mobile. Each card: `bg-ink-2`, sharp corners, `p-8`, top-left icon block (48px, `bg-ink-3`, flame icon + acid accent dot), title (`font-display`, 24px), description (white/70). Cards:
   1. **AI Rapid Prototyping** — Generate a working MVP from a written idea brief.
   2. **Built-in User Testing** — Recruit testers and run structured validation sessions in-app.
   3. **Launch Analytics** — Track signups, engagement, and qualitative feedback in one dashboard.
   4. **Guided Validation** — Step-by-step playbook: problem interviews, smoke tests, concierge MVPs.
   5. **No-Code Required** — Build, iterate, and ship without writing a line of code.
   6. **Iterate with Data** — Decide what to build next from real user signals, not gut feel.

4. **Pricing (`components/Pricing.tsx`)** — `id="pricing"`, `bg-ink-2`, `py-32`. H2 "Simple pricing. Real plans." Three tier cards in `md:grid-cols-3 gap-6`. Each card: `bg-ink`, sharp, `p-8`, flex column. Middle (Pro) card gets `ring-2 ring-flame` and an acid "MOST POPULAR" tag at top. Tiers:
   - **Free — $0/mo.** Validate your idea. Includes: AI idea brief generator, 1 active project, guided validation playbook, community support.
   - **Pro — $29/mo.** Full MVP builder. Includes: everything in Free, unlimited AI prototyping, built-in user testing, launch analytics, priority support. CTA: "Start validating."
   - **Team — $79/mo.** Collaborate. Includes: everything in Pro, up to 5 seats, shared workspaces, role-based permissions, team analytics. CTA: "Bring your team."
   - Footnote in `text-white/40`: "Prices in USD. Annual billing saves 20%."

5. **FAQ (`components/FAQ.tsx`)** — `id="faq"`, `bg-ink`, `py-32`. H2 "Questions, answered." Centered max-w-3xl. 6 items in a stack, each is a native `<details>` with `<summary>` styled as a sharp row (`border-b border-white/10`, py-5, flex justify-between, flame `+`/`−` indicator that rotates). Items:
   1. **What is Uncle Inc.?** — An AI-assisted MVP development platform that helps non-technical founders validate and build startup ideas in days.
   2. **Who is it for?** — First-time and pre-PMF founders, solo or in small teams, who want validation before they commit to building.
   3. **Do I need to know how to code?** — No. Uncle is no-code by default. You describe what you want, the AI builds it.
   4. **How is it different from other no-code tools?** — Uncle starts with validation. Most tools start with building. We help you confirm demand before you spend time building.
   5. **What about pricing?** — Free to validate. $29/mo for the full builder. $79/mo for teams. Annual billing saves 20%.
   6. **When can I start?** — We're in private beta now. Join the waitlist to get early access.

6. **CTA (`components/CTA.tsx`)** — `id="waitlist"`, full-bleed dark section with a flame→magenta diagonal gradient block on the right (40% width, fades left). H2 (Archivo Black, white): "Stop Guessing. Start Validating." Subtext: "Join the waitlist for early access." A single inline form: email input (`bg-ink`, sharp, white text, `placeholder-white/30`, `flex-1`) + flame "Join Waitlist" button. Below form, a small `text-white/50` line: "Early access opens to waitlist members first. No spam, unsubscribe anytime." Form is a `<form action="mailto:waitlist@uncle.inc" method="post">` placeholder with `onSubmit` (client component) that prevents default and shows a `text-acid` confirmation "You're on the list ✓" inline. **Note:** the research did not provision a real waitlist backend; the form uses a local state confirmation with a clear `data-waitlist-endpoint` attribute on the `<form>` so a future Supabase insert can be wired in without changing the UI.

7. **Footer (`components/Footer.tsx`)** — `bg-ink-3`, `py-12`. Row: left "© 2026 Uncle Inc. All rights reserved." in `text-white/50`; right links: `Privacy`, `Terms`, `Contact` (anchors to `#` placeholders). No social icons (no fake accounts).

## 4. USER FLOWS
**Flow A — Primary conversion (visitor → waitlist):**
1. Land on `/` → hero loads.
2. Scroll or click "Join Waitlist" in nav → smooth-scroll to `#waitlist`.
3. Enter email → click button → inline confirmation "You're on the list ✓" replaces form.
4. (Alt) Click "See How It Works" → smooth-scroll to `#features` → read cards → click "Join Waitlist" in nav or CTA.

**Flow B — Objection handling:**
1. Visitor lands skeptical → scrolls past hero to `#pricing` → reads real prices → moves to `#faq` → expands "Do I need to know how to code?" → click FAQ row or nav CTA → reaches `#waitlist`.

**States:** Hover (button invert, link underline), focus-visible (2px acid outline on all interactive elements), reduced-motion (disables hero fade), mobile nav collapses center links behind a checkbox-toggled drawer (no JS, pure CSS via `<details>`).

## 5. PAGES / ROUTES
- **`app/layout.tsx`** — Root layout, sets `<html lang="en">`, loads Inter + Archivo Black from `next/font/google`, applies `font-sans` to body, smooth scroll, metadata (title, description, theme-color `#0a0a0f`).
- **`app/page.tsx`** — Server component, renders `<Nav /> <Hero /> <Features /> <Pricing /> <FAQ /> <CTA /> <Footer />` in order.
- **`app/globals.css`** — Tailwind layers, CSS custom properties `--brand-ink / --brand-flame / --brand-magenta / --brand-acid`, `html { scroll-behavior: smooth }`, reduced-motion media query disables fade, focus-visible ring styles.

(No additional routes — this is a single-page marketing site. The product itself is out of scope for this build.)

## 6. CORE FEATURES
Each is a concrete, working piece of the landing page — not placeholders.

1. **Sticky brand nav with anchor CTAs** — `position: sticky; top: 0`, backdrop blur, three anchor links + one flame CTA that scrolls to `#waitlist`. On `<md`, center links collapse into a pure-CSS drawer (checkbox hack) so the page works without JS.
2. **Hero with oversized display headline** — Archivo Black, fluid `clamp(3.5rem, 8vw, 7rem)`, animated underline SVG on the word "Validate" (flame), single primary + secondary CTA, no fabricated metrics.
3. **6-card feature grid** — 3×2 responsive grid, each card has a custom inline-SVG icon (flame fill + acid accent), title, description. Implemented as a typed array in the component to keep the markup data-driven.
4. **3-tier pricing section** — Real dollar amounts ($0, $29, $79), feature lists, "MOST POPULAR" tag on Pro, Pro card ringed in flame, annual-billing footnote.
5. **Accordion FAQ** — 6 native `<details>` items, no JS expand/collapse, custom `+`/`−` indicator styled via `details[open]` CSS.
6. **Waitlist email capture** — Email input + submit, client-side `onSubmit` handler shows inline acid confirmation, `data-waitlist-endpoint` attribute ready for future Supabase wiring. Form validates email shape (HTML5 `type="email" required`).
7. **Footer with legal placeholders** — Copyright, three text links to `#` anchors, no fake socials.
8. **Accessibility & motion** — Semantic landmarks (`<header> <nav> <main> <section> <footer>`), `aria-expanded` on FAQ summaries (via `<details>`), focus-visible rings, `prefers-reduced-motion` respected.

## 7. DATA MODEL
No backend for this build. Local TypeScript types inside components:

- **`Feature`** `{ id: string; title: string; description: string; icon: 'prototype' | 'testing' | 'analytics' | 'playbook' | 'nocode' | 'iterate' }`
- **`PricingTier`** `{ id: 'free' | 'pro' | 'team'; name: string; price: string; cadence: string; tagline: string; features: string[]; cta: string; highlighted?: boolean; badge?: string }`
- **`FAQItem`** `{ id: string; question: string; answer: string }`
- **`NavLink`** `{ label: string; href: string }`

`components/Features.tsx`, `components/Pricing.tsx`, `components/FAQ.tsx`, and `components/Nav.tsx` each export a `const` array of the above types, mapped to JSX. Keeping data in the component keeps the page statically renderable with no fetches.

## 8. AUTH
Not applicable for the marketing landing page itself. The page contains no login, no user accounts, no protected routes. The single form (waitlist email) is unauthenticated and stores email in client state only for this build — a `data-waitlist-endpoint` attribute marks the integration seam for a future Supabase `waitlist` table (`{ id uuid, email text unique, created_at timestamptz }`) that can be added later without UI changes. **No Clerk, no social buttons, no OAuth.**

## 9. FILES
Concrete file tree, each with a one-line purpose:

```
package.json                                    # Next 14, React 18, Tailwind, TypeScript deps
next.config.js                                  # Standard Next config, no special rewrites
tsconfig.json                                   # Standard TS config, paths "@/*"
tailwind.config.ts                              # Tailwind config, brand colors, font families
postcss.config.js                               # tailwindcss + autoprefixer
app/layout.tsx                                  # Root layout, fonts, metadata, smooth scroll
app/globals.css                                 # Tailwind layers, brand CSS vars, focus rings
app/page.tsx                                    # Server component, composes Nav→Hero→Features→Pricing→FAQ→CTA→Footer
components/Nav.tsx                              # Sticky nav, anchor links, mobile CSS drawer
components/Hero.tsx                             # 'use client', oversized headline, dual CTA
components/Features.tsx                         # 3x2 feature grid, typed Feature[] data
components/Pricing.tsx                          # 3 tiers, Pro highlighted, annual footnote
components/FAQ.tsx                              # 6 <details> items, custom + / − indicator
components/CTA.tsx                              # 'use client', email form + inline confirmation
components/Footer.tsx                           # Copyright + Privacy/Terms/Contact links
```

## 10. ACCEPTANCE
Done = all of the following are true:

- [ ] `npm install` then `npm run dev` starts the app on `:3000` with no errors or warnings.
- [ ] `app/page.tsx` renders all 7 sections in order: Nav, Hero, Features, Pricing, FAQ, CTA, Footer.
- [ ] Brand colors present: `#0a0a0f` page bg, `#ff6b35` primary, `#e91e8c` accent gradient, `#b8ff3a` "popular" tag + check accents, white text.
- [ ] Typography: Inter (body, `font-sans`) and Archivo Black (display, `font-display`) loaded via `next/font/google`; hero headline visibly oversized and uses Archivo Black.
- [ ] Hero shows the exact headline "Validate Your Startup Idea Before You Build It" with a flame underline on "Validate", plus "Join Waitlist" and "See How It Works" buttons. No fake stats, no user counts, no testimonials, no logos.
- [ ] Features grid shows exactly 6 cards with the named titles (AI Rapid Prototyping, Built-in User Testing, Launch Analytics, Guided Validation, No-Code Required, Iterate with Data), each with icon + title + description, on a dark card surface.
- [ ] Pricing shows 3 tiers with prices `$0`, `$29/mo`, `$79/mo`; Pro card has flame ring + "MOST POPULAR" acid badge; each tier has a feature list and a CTA.
- [ ] FAQ shows exactly 6 questions in the specified order, accordion expand/collapse works without JS, indicators toggle `+`/`−`.
- [ ] CTA section has headline "Stop Guessing. Start Validating.", an email input, and a flame "Join Waitlist" button; submitting with a valid email swaps the form for an inline acid confirmation; a small early-access note appears below.
- [ ] Nav is sticky, contains "Uncle Inc." wordmark, anchor links to `#features`, `#pricing`, `#faq`, and a flame "Join Waitlist" button that scrolls to `#waitlist`.
- [ ] Smooth scroll works for all anchor links; focus-visible outline (acid, 2px) is visible on Tab through all interactive elements.
- [ ] Footer shows "© 2026 Uncle Inc. All rights reserved." and Privacy / Terms / Contact text links.
- [ ] `<html lang="en">`, semantic landmarks, no console errors, no `any` leakage, no fake social proof anywhere on the page.
- [ ] `prefers-reduced-motion: reduce` disables the hero fade-in.

FILES: ["package.json", "next.config.js", "tsconfig.json", "tailwind.config.ts", "postcss.config.js", "app/layout.tsx", "app/globals.css", "app/page.tsx", "components/Nav.tsx", "components/Hero.tsx", "components/Features.tsx", "components/Pricing.tsx", "components/FAQ.tsx", "components/CTA.tsx", "components/Footer.tsx"]# Uncle Inc. — Build Plan

## 1. PRODUCT
A Next.js 14 App Router marketing landing page for **Uncle Inc.**, an AI-assisted MVP development platform aimed at non-technical first-time founders. The site has one job: convert qualified visitors into a "Join Waitlist" email capture. The hero pitch — *Validate Your Startup Idea Before You Build It* — directly addresses the ICP's core pain (building something nobody wants) and frames Uncle as a structured validation+build pipeline rather than another no-code toy. Research confirms a saturated solo-freelancer invoice-dunning category and a parallel underserved segment of pre-PMF founders who over-invest in code; the page is built to position Uncle as the disciplined alternative to "just launch and pray."

## 2. WHO IT'S FOR
**Primary ICP:** Non-technical, first-time, pre-PMF startup founders, solo or in tiny teams, aged ~25–45, who have a hypothesis and a weekend of momentum but no validation discipline. They are time-poor, skeptical of fluff, allergic to fake social proof, and decide in 10 seconds whether to scroll or stop. They respond to:
- Concrete, jargon-light language ("validate before you build," not "synergize your go-to-market").
- Visible structure (named sections, real feature names, real prices).
- Honesty — empty counters and invented logos would actively repel this persona.

**Design implications:** oversized type that reads in 3 seconds, one primary CTA repeating across the page, no carousel, no popups, no chat widget, real prices listed, FAQ that answers objections directly.

## 3. LOOK & FEEL

**Visual system:**
- **Vibe:** Bold Frontier. Confident, opinionated, dark, slightly punk. Sharp 0px border-radius on cards, buttons, and inputs. No drop shadows, no glassmorphism, no gradients except a single magenta→flame accent used sparingly on the CTA section.
- **Palette (Tailwind `brand`):** `ink #0a0a0f` (page bg), `flame #ff6b35` (primary CTA, accents), `magenta #e91e8c` (highlight, gradient partner), `acid #b8ff3a` (secondary accent, "popular" tag, check icons), `white #ffffff` (body text), `ink-2 #14141b` (card bg), `ink-3 #1c1c26` (elevated surface / nav).
- **Typography:** Body = Inter (Google Fonts, variable). Headlines = **Archivo Black** (Google Fonts) — chunky, geometric, oversized. Tailwind families: `font-sans` (Inter) and `font-display` (Archivo Black). Hero headline clamps ~56px → 112px across breakpoints; section H2s ~40px → 64px; body 16–18px.
- **Spacing/layout:** Max content width 1200px, generous vertical rhythm — each section is `py-24 md:py-32`. 12-col grid feel via simple flex/grids; cards use `gap-6`.
- **Iconography:** Inline SVG, 1.5px stroke, 24px default. No icon library dependency. Each feature gets a custom 2-color glyph (flame + acid) on a `ink-3` square with sharp corners.
- **Imagery:** None. Pure type, color blocks, and iconography — this is honest, fast, and on-brand for a pre-launch product.
- **Motion:** Reduced. CSS-only fade-in on hero text via `animation-delay` (no framer-motion dep). Smooth scroll globally. Buttons get a 1-frame invert on hover (acid bg / ink text). Accordion uses `<details>` for zero-JS expand/collapse.

**Screens (sections), top to bottom:**

1. **Nav (`components/Nav.tsx`)** — Sticky, `bg-ink-3/90 backdrop-blur`, `border-b border-white/5`. Left: "Uncle Inc." wordmark in `font-display` with a small flame-orange square dot. Center: `Features`, `Pricing`, `FAQ` as anchor links. Right: `Join Waitlist` button (flame bg, ink text, sharp). On scroll past 64px, nav adds a subtle bottom border glow.

2. **Hero (`components/Hero.tsx`)** — Full-width `min-h-[88vh]`, `bg-ink`. Top-left tiny tag: "PRE-LAUNCH · 2026" in acid. Centered headline (Archivo Black): "Validate Your Startup Idea Before You Build It" with the word "Validate" underlined in flame via a hand-drawn-feel SVG stroke. Subtext (Inter, 20px, `text-white/70`, max-w-2xl): "Uncle is an AI-assisted platform that helps non-technical founders go from idea to validated MVP in days, not months — no code required." Two buttons: primary flame "Join Waitlist" (scrolls to #waitlist), secondary outline "See How It Works" (scrolls to #features). No stats row. A small `text-white/40` line: "Currently in private beta."

3. **Features (`components/Features.tsx`)** — `id="features"`, `bg-ink`, `py-32`. Eyebrow "WHAT YOU GET" (acid, uppercase, tracked), H2 "Everything you need. Nothing you don't." 3×2 grid of cards on `md:grid-cols-3`, single column on mobile. Each card: `bg-ink-2`, sharp corners, `p-8`, top-left icon block (48px, `bg-ink-3`, flame icon + acid accent dot), title (`font-display`, 24px), description (white/70). Cards:
   1. **AI Rapid Prototyping** — Generate a working MVP from a written idea brief.
   2. **Built-in User Testing** — Recruit testers and run structured validation sessions in-app.
   3. **Launch Analytics** — Track signups, engagement, and qualitative feedback in one dashboard.
   4. **Guided Validation** — Step-by-step playbook: problem interviews, smoke tests, concierge MVPs.
   5. **No-Code Required** — Build, iterate, and ship without writing a line of code.
   6. **Iterate with Data** — Decide what to build next from real user signals, not gut feel.

4. **Pricing (`components/Pricing.tsx`)** — `id="pricing"`, `bg-ink-2`, `py-32`. H2 "Simple pricing. Real plans." Three tier cards in `md:grid-cols-3 gap-6`. Each card: `bg-ink`, sharp, `p-8`, flex column. Middle (Pro) card gets `ring-2 ring-flame` and an acid "MOST POPULAR" tag at top. Tiers:
   - **Free — $0/mo.** Validate your idea. Includes: AI idea brief generator, 1 active project, guided validation playbook, community support.
   - **Pro — $29/mo.** Full MVP builder. Includes: everything in Free, unlimited AI prototyping, built-in user testing, launch analytics, priority support. CTA: "Start validating."
   - **Team — $79/mo.** Collaborate. Includes: everything in Pro, up to 5 seats, shared workspaces, role-based permissions, team analytics. CTA: "Bring your team."
   - Footnote in `text-white/40`: "Prices in USD. Annual billing saves 20%."

5. **FAQ (`components/FAQ.tsx`)** — `id="faq"`, `bg-ink`, `py-32`. H2 "Questions, answered." Centered max-w-3xl. 6 items in a stack, each is a native `<details>` with `<summary>` styled as a sharp row (`border-b border-white/10`, py-5, flex justify-between, flame `+`/`−` indicator that rotates). Items:
   1. **What is Uncle Inc.?** — An AI-assisted MVP development platform that helps non-technical founders validate and build startup ideas in days.
   2. **Who is it for?** — First-time and pre-PMF founders, solo or in small teams, who want validation before they commit to building.
   3. **Do I need to know how to code?** — No. Uncle is no-code by default. You describe what you want, the AI builds it.
   4. **How is it different from other no-code tools?** — Uncle starts with validation. Most tools start with building. We help you confirm demand before you spend time building.
   5. **What about pricing?** — Free to validate. $29/mo for the full builder. $79/mo for teams. Annual billing saves 20%.
   6. **When can I start?** — We're in private beta now. Join the waitlist to get early access.

6. **CTA (`components/CTA.tsx`)** — `id="waitlist"`, full-bleed dark section with a flame→magenta diagonal gradient block on the right (40% width, fades left). H2 (Archivo Black, white): "Stop Guessing. Start Validating." Subtext: "Join the waitlist for early access." A single inline form: email input (`bg-ink`, sharp, white text, `placeholder-white/30`, `flex-1`) + flame "Join Waitlist" button. Below form, a small `text-white/50` line: "Early access opens to waitlist members first. No spam, unsubscribe anytime." Form is a `<form action="mailto:waitlist@uncle.inc" method="post">` placeholder with `onSubmit` (client component) that prevents default and shows a `text-acid` confirmation "You're on the list ✓" inline. **Note:** the research did not provision a real waitlist backend; the form uses a local state confirmation with a clear `data-waitlist-endpoint` attribute on the `<form>` so a future Supabase insert can be wired in without changing the UI.

7. **Footer (`components/Footer.tsx`)** — `bg-ink-3`, `py-12`. Row: left "© 2026 Uncle Inc. All rights reserved." in `text-white/50`; right links: `Privacy`, `Terms`, `Contact` (anchors to `#` placeholders). No social icons (no fake accounts).

## 4. USER FLOWS
**Flow A — Primary conversion (visitor → waitlist):**
1. Land on `/` → hero loads.
2. Scroll or click "Join Waitlist" in nav → smooth-scroll to `#waitlist`.
3. Enter email → click button → inline confirmation "You're on the list ✓" replaces form.
4. (Alt) Click "See How It Works" → smooth-scroll to `#features` → read cards → click "Join Waitlist" in nav or CTA.

**Flow B — Objection handling:**
1. Visitor lands skeptical → scrolls past hero to `#pricing` → reads real prices → moves to `#faq` → expands "Do I need to know how to code?" → click FAQ row or nav CTA → reaches `#waitlist`.

**States:** Hover (button invert, link underline), focus-visible (2px acid outline on all interactive elements), reduced-motion (disables hero fade), mobile nav collapses center links behind a checkbox-toggled drawer (no JS, pure CSS via `<details>`).

## 5. PAGES / ROUTES
- **`app/layout.tsx`** — Root layout, sets `<html lang="en">`, loads Inter + Archivo Black from `next/font/google`, applies `font-sans` to body, smooth scroll, metadata (title, description, theme-color `#0a0a0f`).
- **`app/page.tsx`** — Server component, renders `<Nav /> <Hero /> <Features /> <Pricing /> <FAQ /> <CTA /> <Footer />` in order.
- **`app/globals.css`** — Tailwind layers, CSS custom properties `--brand-ink / --brand-flame / --brand-magenta / --brand-acid`, `html { scroll-behavior: smooth }`, reduced-motion media query disables fade, focus-visible ring styles.

(No additional routes — this is a single-page marketing site. The product itself is out of scope for this build.)

## 6. CORE FEATURES
Each is a concrete, working piece of the landing page — not placeholders.

1. **Sticky brand nav with anchor CTAs** — `position: sticky; top: 0`, backdrop blur, three anchor links + one flame CTA that scrolls to `#waitlist`. On `<md`, center links collapse into a pure-CSS drawer (checkbox hack) so the page works without JS.
2. **Hero with oversized display headline** — Archivo Black, fluid `clamp(3.5rem, 8vw, 7rem)`, animated underline SVG on the word "Validate" (flame), single primary + secondary CTA, no fabricated metrics.
3. **6-card feature grid** — 3×2 responsive grid, each card has a custom inline-SVG icon (flame fill + acid accent), title, description. Implemented as a typed array in the component to keep the markup data-driven.
4. **3-tier pricing section** — Real dollar amounts ($0, $29, $79), feature lists, "MOST POPULAR" tag on Pro, Pro card ringed in flame, annual-billing footnote.
5. **Accordion FAQ** — 6 native `<details>` items, no JS expand/collapse, custom `+`/`−` indicator styled via `details[open]` CSS.
6. **Waitlist email capture** — Email input + submit, client-side `onSubmit` handler shows inline acid confirmation, `data-waitlist-endpoint` attribute ready for future Supabase wiring. Form validates email shape (HTML5 `type="email" required`).
7. **Footer with legal placeholders** — Copyright, three text links to `#` anchors, no fake socials.
8. **Accessibility & motion** — Semantic landmarks (`<header> <nav> <main> <section> <footer>`), `aria-expanded` on FAQ summaries (via `<details>`), focus-visible rings, `prefers-reduced-motion` respected.

## 7. DATA MODEL
No backend for this build. Local TypeScript types inside components:

- **`Feature`** `{ id: string; title: string; description: string; icon: 'prototype' | 'testing' | 'analytics' | 'playbook' | 'nocode' | 'iterate' }`
- **`PricingTier`** `{ id: 'free' | 'pro' | 'team'; name: string; price: string; cadence: string; tagline: string; features: string[]; cta: string; highlighted?: boolean; badge?: string }`
- **`FAQItem`** `{ id: string; question: string; answer: string }`
- **`NavLink`** `{ label: string; href: string }`

`components/Features.tsx`, `components/Pricing.tsx`, `components/FAQ.tsx`, and `components/Nav.tsx` each export a `const` array of the above types, mapped to JSX. Keeping data in the component keeps the page statically renderable with no fetches.

## 8. AUTH
Not applicable for the marketing landing page itself. The page contains no login, no user accounts, no protected routes. The single form (waitlist email) is unauthenticated and stores email in client state only for this build — a `data-waitlist-endpoint` attribute marks the integration seam for a future Supabase `waitlist` table (`{ id uuid, email text unique, created_at timestamptz }`) that can be added later without UI changes. **No Clerk, no social buttons, no OAuth.**

## 9. FILES
Concrete file tree, each with a one-line purpose:

```
package.json                                    # Next 14, React 18, Tailwind, TypeScript deps
next.config.js                                  # Standard Next config, no special rewrites
tsconfig.json                                   # Standard TS config, paths "@/*"
tailwind.config.ts                              # Tailwind config, brand colors, font families
postcss.config.js                               # tailwindcss + autoprefixer
app/layout.tsx                                  # Root layout, fonts, metadata, smooth scroll
app/globals.css                                 # Tailwind layers, brand CSS vars, focus rings
app/page.tsx                                    # Server component, composes Nav→Hero→Features→Pricing→FAQ→CTA→Footer
components/Nav.tsx                              # Sticky nav, anchor links, mobile CSS drawer
components/Hero.tsx                             # 'use client', oversized headline, dual CTA
components/Features.tsx                         # 3x2 feature grid, typed Feature[] data
components/Pricing.tsx                          # 3 tiers, Pro highlighted, annual footnote
components/FAQ.tsx                              # 6 <details> items, custom + / − indicator
components/CTA.tsx                              # 'use client', email form + inline confirmation
components/Footer.tsx                           # Copyright + Privacy/Terms/Contact links
```

## 10. ACCEPTANCE
Done = all of the following are true:

- [ ] `npm install` then `npm run dev` starts the app on `:3000` with no errors or warnings.
- [ ] `app/page.tsx` renders all 7 sections in order: Nav, Hero, Features, Pricing, FAQ, CTA, Footer.
- [ ] Brand colors present: `#0a0a0f` page bg, `#ff6b35` primary, `#e91e8c` accent gradient, `#b8ff3a` "popular" tag + check accents, white text.
- [ ] Typography: Inter (body, `font-sans`) and Archivo Black (display, `font-display`) loaded via `next/font/google`; hero headline visibly oversized and uses Archivo Black.
- [ ] Hero shows the exact headline "Validate Your Startup Idea Before You Build It" with a flame underline on "Validate", plus "Join Waitlist" and "See How It Works" buttons. No fake stats, no user counts, no testimonials, no logos.
- [ ] Features grid shows exactly 6 cards with the named titles (AI Rapid Prototyping, Built-in User Testing, Launch Analytics, Guided Validation, No-Code Required, Iterate with Data), each with icon + title + description, on a dark card surface.
- [ ] Pricing shows 3 tiers with prices `$0`, `$29/mo`, `$79/mo`; Pro card has flame ring + "MOST POPULAR" acid badge; each tier has a feature list and a CTA.
- [ ] FAQ shows exactly 6 questions in the specified order, accordion expand/collapse works without JS, indicators toggle `+`/`−`.
- [ ] CTA section has headline "Stop Guessing. Start Validating.", an email input, and a flame "Join Waitlist" button; submitting with a valid email swaps the form for an inline acid confirmation; a small early-access note appears below.
- [ ] Nav is sticky, contains "Uncle Inc." wordmark, anchor links to `#features`, `#pricing`, `#faq`, and a flame "Join Waitlist" button that scrolls to `#waitlist`.
- [ ] Smooth scroll works for all anchor links; focus-visible outline (acid, 2px) is visible on Tab through all interactive elements.
- [ ] Footer shows "© 2026 Uncle Inc. All rights reserved." and Privacy / Terms / Contact text links.
- [ ] `<html lang="en">`, semantic landmarks, no console errors, no `any` leakage, no fake social proof anywhere on the page.
- [ ] `prefers-reduced-motion: reduce` disables the hero fade-in.

FILES: ["package.json", "next.config.js", "tsconfig.json", "tailwind.config.ts", "postcss.config.js", "app/layout.tsx", "app/globals.css", "app/page.tsx", "components/Nav.tsx", "components/Hero.tsx", "components/Features.tsx", "components/Pricing.tsx", "components/FAQ.tsx", "components/CTA.tsx", "components/Footer.tsx"]