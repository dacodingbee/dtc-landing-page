# dtc-landing-page

A Claude Code skill that builds high-converting landing pages for DTC and e-commerce brands. It produces self-contained HTML artifacts you can preview, iterate on, and deploy.

## What makes this different from "make me a landing page"

Most AI-generated landing pages look fine and convert poorly. This skill encodes the copy strategy that separates pages that sell from pages that just exist:

- **Fact-locking.** Prices, dates, and URLs are loaded from reference files, never invented. A wrong price on a live page is a refund conversation.
- **Traffic-source awareness.** Different copy strategy depending on whether the visitor came from email, paid social, search, or an influencer. The email already did the emotional work. The page sells the specifics.
- **Structured objection handling.** Every page addresses the real hesitations for that price point, not generic FAQ filler.
- **Message match enforcement.** The hero echoes the language from the ad or email that drove the click. The transition should feel seamless.
- **Pre-ship checklist.** Catches wrong prices, missing URLs, broken mobile layouts, and urgency theater before you deploy.

## Install

Copy the skill into your Claude Code skills directory:

```bash
# Global (available in all projects)
cp -r SKILL.md ~/.claude/skills/dtc-landing-page/SKILL.md

# Or project-level (available only in one project)
cp -r SKILL.md your-project/.claude/skills/dtc-landing-page/SKILL.md
```

## Usage

In Claude Code, invoke the skill:

```
/dtc-landing-page
```

Or just ask Claude to build a landing page and it will activate automatically when it matches the trigger phrases: "landing page", "LP", "campaign page", "product page", "launch page", or requests to turn an email/ad into a page.

### Minimal (no setup)

Just invoke the skill. Claude will ask you for the product details, pricing, CTA URL, brand colors, and traffic source.

### With reference files (recommended)

Create a `references/` directory in the skill folder for your brand:

```
~/.claude/skills/dtc-landing-page/
  references/
    brand.md     # Voice, tone, positioning, banned phrasings
    offers.md    # Locked prices, dates, URLs, product facts
    design.md    # Colors, fonts, spacing
```

The skill reads these on every invocation. See `examples/references/` for templates.

### Per-project overrides

For project-specific campaigns, create the same files in your project:

```
your-project/.claude/skills/dtc-landing-page/
  references/
    brand.md
    offers.md
    design.md
```

Project-level references take precedence over global ones.

## What it produces

A self-contained HTML page published as a Claude Code artifact. The page:

- Is mobile-first (assumes 70%+ mobile traffic)
- Uses CSS custom properties for easy re-theming
- Has no external dependencies (works offline, loads instantly)
- Includes image placeholders with descriptive comments for replacement
- Supports anchor links for deep-linking from emails/ads to specific sections

## Page structure

The skill uses a section order optimized for high-consideration DTC purchases ($50+):

1. **Hero** with key facts above the fold
2. **What you get** (the highest-leverage section: make them picture the product)
3. **Who's behind it** (founder/team credentials)
4. **Social proof** (real customer language, not filler)
5. **Objection handling** (FAQ addressing real hesitations)
6. **Risk reversal** (return policy, guarantee)
7. **Secondary offers** (lower-commitment alternatives)
8. **Final CTA** (restate key facts, close)

## Composable with other skills

- `cro` for auditing an existing page
- `ads-landing` for post-click quality scoring
- `copy-editing` for line-level polish
- `copywriting` for generic copy (this skill overrides it for landing pages)

## Contributing

PRs welcome. If you've used this for a vertical not covered well by the defaults (B2B services, SaaS, physical retail), open an issue or PR with the adaptations that worked.

## License

MIT
