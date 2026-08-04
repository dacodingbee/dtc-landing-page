---
name: dtc-landing-page
description: "Build high-converting landing pages for DTC and e-commerce brands. Produces self-contained HTML artifacts. Use when the user says 'landing page', 'LP', 'campaign page', 'product page', 'launch page', or asks to turn an email/ad into a page. Loads locked offer facts and brand voice from references/ so prices, dates, and links are never invented. For auditing an existing page, use cro or ads-landing instead."
metadata:
  version: 1.0.0
  author: dacodingbee
  repo: https://github.com/dacodingbee/dtc-landing-page
---

# DTC Landing Page Builder

You are building a conversion landing page for a direct-to-consumer brand. This skill produces a self-contained HTML page as an artifact. It encodes the copy strategy, fact-locking, and page structure that separate pages that convert from pages that just look nice.

## Step 0: Load the facts. Never invent them.

Before writing a single line, look for reference files. Check in order:

1. `references/` in this skill's directory (`~/.claude/skills/dtc-landing-page/references/`)
2. `Skills/dtc-landing-page/references/` in the project
3. `Context/brand.md` in the project (for vault-based projects)

| What | File |
|---|---|
| Offers, prices, dates, deadlines, URLs | `references/offers.md` |
| Voice, tone, positioning, banned phrasings | `references/brand.md` |
| Colors, fonts, spacing, component styles | `references/design.md` |

If a reference file exists, **read it in full before writing. Not a sample. All of it.**

If a price, date, or URL is not in a reference file or explicitly provided by the user, **stop and ask.** Do not approximate. A wrong price on a live page is a refund conversation.

> When multiple sources exist (e.g., an offers file and a recent email draft), sort by date. Newest wins. Reconcile the offers file to match before writing a word of copy.

If no reference files exist, ask the user for:
1. Product/offer name, price, and key facts
2. CTA destination URL
3. Brand colors (or "use a clean default")
4. Traffic source (where visitors come from)

## Step 1: Decide the page type

Ask if not obvious:

**Single-offer page**: One product, one event, one service. Most common. One hero, one CTA, everything supports that one conversion.

**Campaign hub page**: A campaign containing multiple offers (e.g., a holiday sale with different bundles, a launch with multiple tiers). The flagship offer gets the hero and dominant CTA. Every other offer gets a real section with a real button, not a footnote. **Anchor every offer section** (`#flagship`, `#starter`, `#gift-set`) so emails and ads can deep-link to the relevant one. Someone who can't afford the flagship is not a lost visitor. They're a starter-kit buyer.

## Step 2: Understand the traffic source

The page's job depends entirely on where the visitor came from. Ask the user if they don't specify.

| Traffic source | What's already done | Page job |
|---|---|---|
| **Email sequence** | Emotional promise made. Visitor clicked because they're interested. | Sell the specifics. Don't re-run the pitch. |
| **Paid social (Meta, TikTok)** | 3-second hook. Visitor is curious but uncommitted. | Earn attention fast. Hero must justify the click in under 5 seconds. |
| **Paid search (Google)** | Visitor has intent. They searched for this. | Match the keyword. Answer the question immediately. |
| **Organic / SEO** | Visitor found you. May not know the brand. | Brand intro + social proof before the ask. |
| **Influencer / affiliate** | Trust transferred from the creator. | Reinforce the creator's framing. Don't contradict their message. |
| **SMS (Attentive, Postscript)** | Short, punchy message. Mobile traffic. | Mobile-first. Fast-loading. Key facts above fold. |

**Message match rule**: the hero headline should echo the language from the traffic source. If someone clicked "Your skin deserves better this summer," the page should not open with "Welcome to our store." The click must feel continuous.

**The upstream already did the emotional work.** If the visitor came from an email or ad that made an emotional promise, the page's job is different. Don't re-run the emotional setup. Someone who clicked is already sold on the feeling and is now asking practical questions: what's in it, how long, what do I bring, can I get a refund, is this worth the price. Re-earning attention that you already have is the single most common landing page failure.

## Step 3: One page, one job

Every landing page gets exactly one primary conversion action. Decide it before writing.

| Conversion type | CTA pattern | Button copy formula |
|---|---|---|
| **Purchase** | Direct buy | "Get [Product] — $[Price]" |
| **Booking** | Calendar/scheduler link | "[Action] Your [Thing], [Date]" |
| **Signup** | Email/SMS capture | "Join [Number] [People] Who [Benefit]" |
| **Waitlist** | Email capture | "Get Early Access to [Thing]" |
| **Download** | Lead magnet | "Get the Free [Asset]" |

Secondary offers may appear below the primary argument, but never with a button that competes visually with the primary CTA.

Ask the user for the primary action if it's not obvious. Then hold the line on it.

## Step 4: Page structure

Use this order. Adapt section content to the product and vertical, but keep the sequence. It is optimized for high-consideration DTC purchases ($50+).

### 1. Hero
- Headline echoing the traffic source
- Key facts visible without scrolling: price, date (if event), or core value prop
- Primary CTA button
- Optional: hero image or product shot
- **Mobile rule**: headline, price/key-fact, and CTA must all be visible without scrolling on a 375px screen

### 2. What you get
The single highest-leverage section. People don't hesitate because they doubt the value. They hesitate because they can't picture what they're buying.

- **Products**: what's in the box, materials, dimensions, how it feels, what it replaces
- **Services**: step-by-step or hour-by-hour walkthrough of the experience
- **Events**: the full agenda. What happens when, what to bring, what to wear
- **Subscriptions**: what arrives, how often, what the first delivery looks like

Concrete beats atmospheric. "A 60-minute deep tissue massage with heated basalt stones" beats "a luxurious spa experience."

### 3. Who's behind it
Named people with real credentials. This is where DTC brands differentiate from marketplace listings.

- Founder story: 2-3 sentences max, focused on why this product exists
- Team credentials if relevant (certifications, years of experience, training)
- Sourcing story: "Made in [place]," "Ingredients from [source]"
- Keep it tight. This is a trust signal, not a biography.

### 4. Social proof
Real customer language only. Do not write testimonial-shaped filler.

- Pull actual reviews, testimonials, or voice-of-customer language if available
- Include specifics: names, locations, timeframes, measurable outcomes
- Numbers: "12,000 customers", "4.8 stars from 2,300 reviews"
- Press mentions or awards if available
- If no real proof exists yet, use a placeholder callout and tell the user to add real testimonials before launch

### 5. Objection handling
Address the real hesitations, not generic ones. FAQ format works well.

Common DTC objections by price tier:
- **Under $50**: "Is this better than [cheaper alternative]?"
- **$50-100**: "Is this worth it vs. what I'm already using?"
- **$100-300**: "What if I don't like it? What's the return policy?"
- **$300+**: "What exactly am I getting for this money? Who else has done this?"
- **Subscription**: "Can I cancel anytime? Am I locked in? How do I skip a month?"
- **Events/Services**: "What should I expect? What if something comes up?"

Ask the user for their specific objections. Every brand knows their top 3-5 hesitations from customer service conversations, support tickets, or abandoned cart surveys.

### 6. Risk reversal
Reduce the perceived risk of converting:
- Return/refund policy. Be specific: "30-day no-questions-asked return" beats "satisfaction guaranteed."
- Money-back guarantee with clear terms
- Free trial or sample option
- "Cancel anytime" for subscriptions
- "What to expect on day one" for services

### 7. Secondary offers (optional)
Lower-commitment alternatives for visitors who bounced off the primary price or commitment level:
- Smaller size or starter kit
- Single purchase vs. subscription
- Waitlist or email signup
- Related but more accessible product

Secondary button styling. These are escape valves, not competitors to the primary CTA. Someone who can't spend the full price is not a lost visitor.

### 8. Final CTA
- Restate the key facts: what they get, the price, any deadline
- Primary CTA button repeated
- Brand tagline or closing line if the brand has one

## Step 5: Voice rules

These are the defaults. Brand-specific overrides from `references/brand.md` always take precedence.

- **Specific over atmospheric.** Concrete details convert. Vibes don't.
- **No urgency theater.** No "only 3 left" unless it's verified and true. No countdown timers unless there's a real, externally imposed deadline. Manufactured scarcity erodes trust faster than it creates conversions.
- **No exclamation points in body copy.** One in the hero headline is acceptable. Zero is better.
- **Translate jargon, don't strip it.** Keep the credibility, lose the confusion. The reader should understand what makes this different without needing a glossary.
- **CTA copy: action verb + what they get.** Good: "Reserve Your Spot, Aug 29", "Get the Starter Kit — $49." Bad: "Learn More," "Submit," "Click Here," "Get Started."
- **No em dashes.** Use periods, commas, colons, or restructure the sentence.

## Step 6: Build the HTML artifact

Produce a self-contained HTML page using the Artifact tool. Before writing, load the `artifact-design` skill for design guidance.

### Design requirements

- **Mobile-first.** Assume 70%+ of DTC traffic is mobile. Design for 375px width first, then scale up.
- **Fast.** No external fonts, CDNs, or scripts. System font stack by default. Embed a custom font as base64 only if critical to the brand identity.
- **Accessible.** Semantic HTML (`<section>`, `<header>`, `<nav>`), sufficient contrast (4.5:1 for body text, 3:1 for large text), proper heading hierarchy (one `<h1>`, sections use `<h2>`), descriptive alt text placeholders for images.
- **Themed with CSS custom properties.** Every brand value (colors, fonts, spacing) defined once in `:root` so the user can reskin the entire page by changing one block.

### CSS custom properties to define

```css
:root {
  --color-primary: ;       /* Brand primary: CTA buttons, key accents */
  --color-secondary: ;     /* Supporting brand color */
  --color-bg: ;            /* Page background */
  --color-surface: ;       /* Card and section backgrounds */
  --color-text: ;          /* Body text */
  --color-text-muted: ;    /* Secondary text, captions */
  --color-cta: ;           /* CTA button background */
  --color-cta-hover: ;     /* CTA button hover state */
  --color-cta-text: ;      /* CTA button text */
  --font-heading: ;        /* Heading font stack */
  --font-body: ;           /* Body font stack */
  --max-width: 960px;      /* Content max width */
  --section-gap: 4rem;     /* Vertical spacing between sections */
}
```

Pull values from `references/design.md` if it exists. Otherwise ask the user for brand colors and fonts, or use a clean neutral default (warm white background, near-black text, one accent color for CTAs).

### Image handling
- Use `<img>` tags with descriptive alt text and a placeholder background color matching the brand palette
- Comment each placeholder: `<!-- REPLACE: hero product shot, 1200x800, show the product in use -->`
- For testimonial photos: use initials in a circle as a CSS-only placeholder

### Anchor links
For campaign hub pages with multiple offers, give each section an `id` attribute so emails and ads can deep-link: `<section id="retreat">`, `<section id="starter-kit">`.

### Sticky CTA (optional)
For long pages (4+ sections), add a subtle sticky bar at the bottom of the viewport on mobile with the primary CTA. It should appear only after the user scrolls past the hero CTA.

## Step 7: Pre-ship checklist

Run this before handing over. Report results honestly. Flag any item you cannot verify.

- [ ] Every price, date, and deadline traced to a reference file or explicit user input
- [ ] Every button URL provided by the user or reference file. No invented links
- [ ] Exactly one primary CTA, visible above the fold on mobile (375px)
- [ ] Hero language matches the traffic source's promise (message match)
- [ ] "What you get" section is concrete and specific, not atmospheric
- [ ] No manufactured scarcity or urgency theater
- [ ] Mobile: hero readable, CTA tappable (min 48px tap target), no horizontal scroll
- [ ] CSS custom properties used for all brand values. User can reskin in one block
- [ ] All image placeholders have descriptive alt text and replacement comments
- [ ] Page is self-contained. No external requests that would fail offline
- [ ] Anchor links work for campaign hub pages (each offer section has an id)
- [ ] Heading hierarchy is correct (one h1, sections use h2)

## Customization

### Adding your brand

Create a `references/` directory in this skill's folder and add your brand files:

```
~/.claude/skills/dtc-landing-page/
  references/
    brand.md     -- Voice, tone, banned phrasings, positioning
    offers.md    -- Locked prices, dates, URLs, product facts
    design.md    -- Colors, fonts, spacing, component styles
```

The skill reads these on every invocation. Update them as your campaigns change.

See `examples/` in the GitHub repo for templates of each file.

### Per-project overrides

For project-specific customization, create the same reference files in your project's skill directory:

```
your-project/.claude/skills/dtc-landing-page/
  references/
    brand.md
    offers.md
    design.md
```

Project-level references override global ones.

## Related skills

- `cro` for auditing an existing page that's underperforming
- `ads-landing` for scoring post-click quality if the page takes paid traffic
- `copy-editing` for a line-level pass after the draft is done
- `copywriting` for generic copy (this skill overrides it for landing pages)
