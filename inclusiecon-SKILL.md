---
name: inclusiecon
description: >
  Use this skill for ANY task involving the INCLUSIECON website (inclusiecon.ca) — including writing output card blurbs, building or editing HTML research pages, adding papers to the research hub, writing drawer entries, building or editing announcements (index or detail pages), handling team/funder attribution, applying SEO meta tags, or working with GitHub raw asset URLs. Trigger on any mention of INCLUSIECON, research-*.html pages, announcement-*.html pages, output cards, announce-cards, pub-entry, drawer-pub, stream tags (FACT/ENABLE), Tedds, Petit, Arshad, or any of the site's research areas (basic income, MVPF, property tax, STR, intersectionality, microsimulation, cash transfers).
---

# INCLUSIECON Site Skill

## Identity & Design System

**Site:** inclusiecon.ca  
**GitHub repo raw URL base:** `https://raw.githubusercontent.com/lmtedds/inclusiecon/main/`  
**PDF links:** Always use GitHub raw URLs — never relative paths for PDFs.  
Example: `https://raw.githubusercontent.com/lmtedds/inclusiecon/main/filename.pdf`

**Fonts:** Lora (serif, headings/titles) + DM Sans (sans-serif, body)  
**CSS variables (always use these, never hardcode hex):**

```css
--primary:         #5c1a1a;   /* deep burgundy */
--primary-dark:    #3e1010;
--primary-mid:     #7a2828;
--primary-light:   #a84848;
--secondary:       #7a3a44;
--secondary-mid:   #9e5560;
--secondary-light: #c48890;
--secondary-pale:  #ecdde0;
--accent:          #a87828;   /* gold */
--accent-light:    #c8a050;
--accent-pale:     #e8d898;
--surface:         #f7f2ea;
--surface-raised:  #ece4d8;
--border:          #ddd0bc;
--text-dark:       #180808;
--text-mid:        #3e2028;
--text-muted:      #7a5858;
```

---

## Research Streams

There are exactly two research streams. Apply them correctly:

| Tag | Meaning | When to use |
|-----|---------|-------------|
| **FACT** | Foundational, descriptive, or measurement-focused research | Empirical data work, mapping, measurement, microsimulation, spatial data |
| **ENABLE** | Policy design, reform analysis, normative evaluation | Program design, welfare analysis, policy recommendations, frameworks |

**Important:** "ENGAGE" is a legacy label — do not use it. The correct label is **ENABLE**.

---

## Site-Wide Navigation Conventions

The site uses **three nav patterns** depending on page type. All three share the same link order and must be kept in sync when new top-level sections are added.

**Canonical link order (left to right):**
`Services · Research · Announcements · Who We Are · Partner With Us · [Contact / Get in Touch]`

Announcements sits right after Research — research news lives next to research.

### Pattern 1: Main pages (`ul/li`, no Home link)
Used on: `index.html`, `services.html`, `research.html`, `who-we-are.html`, `partner-with-us.html`, `contact.html`, `announcements.html`.
The logo is home — no "Home" link. Last item is a gold CTA button: `Get in Touch`.

```html
<ul class="nav-links">
  <li><a href="services.html">Services</a></li>
  <li><a href="research.html">Research</a></li>
  <li><a href="announcements.html">Announcements</a></li>
  <li><a href="who-we-are.html">Who We Are</a></li>
  <li><a href="partner-with-us.html">Partner With Us</a></li>
  <li><a href="contact.html" class="nav-cta">Get in Touch</a></li>
</ul>
```

### Pattern 2: Research sub-pages and announcement detail pages (`div/a`, with Home link)
Used on: all `research-*.html` project pages and all `announcement-*.html` detail pages.
Includes "Home" link. Last item is plain "Contact" (no CTA styling).

```html
<div class="nav-links">
  <a href="index.html">Home</a>
  <a href="services.html">Services</a>
  <a href="research.html">Research</a>
  <a href="announcements.html">Announcements</a>
  <a href="who-we-are.html">Who We Are</a>
  <a href="partner-with-us.html">Partner With Us</a>
  <a href="contact.html">Contact</a>
</div>
```

### Pattern 3: Briefs (`ul/li`, with Home link)
Used on: `bpa-brief.html`, `cash-transfer-brief.html`.
Hybrid — uses `ul/li` like main pages but includes the `Home` link like sub-pages. Plain `Contact` at the end (no CTA).

**Do not mix patterns on a single page.** Matching the existing pattern on the page you are editing is more important than picking one "correct" pattern — the skill file documents what already exists, not what should exist. When adding a new top-level section, update all three patterns across every file.

**Active state:** Add `class="active"` to the link that matches the current page. The logo itself is never an active state target.

---

## Core Team

| Name | Role | Link |
|------|------|-------|
| **Lindsay M. Tedds** | Co-Founder, Professor of Economics, University of Calgary | — |
| **Gillian Petit** | Co-Founder, Senior Research Associate | — |
| **Selvia Arshad** | Co-Investigator, Mitacs Accelerate Intern | [selviaarshad.com](https://selviaarshad.com/) |
| **Anna Cameron** | Research Team (STR Calgary) | — |
| **Alexa Atherly** | Research Team (STR Calgary) | — |
| **Samuel Shipley** | Research Team | LinkedIn link TBC |

**Author name conventions:**
- Always: `Lindsay M. Tedds` (never "Lindsay Tedds")
- Always: `Gillian Petit` (never "G. Petit")
- Selvia Arshad gets a hyperlink whenever mentioned: `<a href="https://selviaarshad.com/" target="_blank" rel="noopener" style="color: inherit; text-decoration: underline; text-underline-offset: 3px;">Selvia Arshad</a>`

---

## Output Card Formats

There are **three card contexts**. Use the right one.

### 1. Project page output card (`output-item`)
Used on individual research pages (e.g. `research-mvpf.html`).

```html
<div class="output-item">
  <div class="output-icon icon-[TYPE]">[EMOJI]</div>
  <div class="output-main">
    <div class="output-title">[FULL PAPER TITLE]</div>
    <div class="output-meta"><strong>[AUTHORS]</strong> · [VENUE] · [YEAR/STATUS]</div>
    <div class="output-blurb">[BLURB — see voice guide below]</div>
    <div class="output-tags">
      <span class="tag tag-[STREAM]">[STREAM]</span>
      <span class="tag tag-[STATUS]">[STATUS]</span>
    </div>
  </div>
  <div class="output-action">
    <!-- If available: -->
    <a href="[URL]" target="_blank" rel="noopener" class="btn-read">Read ↗</a>
    <!-- If forthcoming: -->
    <span class="badge-forthcoming">⏳ Forthcoming</span>
    <!-- If multiple links: -->
    <div class="output-action-multi">
      <a href="[PRIMARY]" target="_blank" rel="noopener" class="btn-read">Read ↗</a>
      <a href="[SECONDARY]" target="_blank" rel="noopener" class="btn-read-secondary">📋 Brief</a>
    </div>
  </div>
</div>
```

**Icon classes and emoji by output type:**
| Type | Class | Emoji |
|------|-------|-------|
| Journal article | `icon-forthcoming` | 📄 |
| Commentary / policy forum | `icon-commentary` | 💬 |
| Book / book chapter | `icon-forthcoming` | 📕 |
| Brief / report | `icon-brief` | 📋 |
| Poster / visual | `icon-brief` | 🖼️ |
| Video / audio | `icon-forthcoming` | 🎥 |

**Tag classes:**
| Tag | Class |
|-----|-------|
| ENABLE | `tag-enable` |
| FACT | `tag-fact` |
| Available | `tag-available` |
| Forthcoming | `tag-forthcoming` |

---

### 2. Research hub pub-entry card (`pub-entry`)
Used on `research.html` — the main research listing page. These are larger cards with a decorative SVG header image, stream pill, and pub-actions row.

```html
<div class="pub-entry" data-stream="[enable|fact]" data-type="[journal|report|book|commentary]">
  <div class="pub-img-wrap">
    <svg class="pub-img-bg" viewBox="0 0 600 160" xmlns="http://www.w3.org/2000/svg" preserveAspectRatio="xMidYMid slice">
      <!-- decorative SVG — abstract data/policy visual, dark background -->
    </svg>
    <div class="pub-img-overlay"></div>
  </div>
  <div class="pub-body">
    <div class="pub-meta">
      <span class="pub-stream-pill psp-[enable|fact]">[ENABLE|FACT]</span>
      <span class="pub-type">[TYPE LABEL]</span>
      <span class="pub-year">[YEAR]</span>
    </div>
    <div class="pub-title">[FULL PAPER TITLE]</div>
    <div class="pub-authors"><strong>[AUTHORS]</strong></div>
    <div class="pub-outlet">[JOURNAL/VENUE] · [DOI or date if available]</div>
    <div class="pub-blurb">[BLURB — see voice guide below]</div>
    <div class="pub-actions">
      <a href="[URL]" target="_blank" rel="noopener" class="pub-link">Read [Article/Report/Study] ↗</a>
      <!-- optional secondary links: -->
      <a href="[URL]" target="_blank" rel="noopener" class="pub-link-secondary">📋 Brief</a>
      <a href="[URL]" target="_blank" rel="noopener" class="pub-link-secondary">📊 Poster</a>
      <a href="[URL]" target="_blank" rel="noopener" class="pub-link-secondary">🎥 Video</a>
      <!-- optional drawer button: -->
      <button class="pub-drawer-btn" onclick="openDrawer('drawer-[id]')">📚 Publications <span class="btn-count">[N]</span></button>
    </div>
  </div>
</div>
```

---

### 3. Drawer pub entry (`drawer-pub`)
Used inside `<aside class="drawer">` panels on `research.html`. Compact format, no images.

```html
<div class="drawer-pub">
  <div class="drawer-pub-meta">
    <span class="drawer-pub-type">[TYPE]</span>
    <span class="drawer-pub-year">[YEAR or Forthcoming]</span>
  </div>
  <div class="drawer-pub-title">[FULL PAPER TITLE]</div>
  <div class="drawer-pub-authors"><strong>[AUTHORS]</strong></div>
  <div class="drawer-pub-outlet">[VENUE] · [DOI/DATE if available]</div>
  <div class="drawer-pub-blurb">[BLURB — shorter, 1–2 sentences ok]</div>
  <div class="drawer-pub-actions">
    <a href="[URL]" target="_blank" rel="noopener" class="drawer-pub-link">Read ↗</a>
    <!-- optional secondary: -->
    <a href="[URL]" target="_blank" rel="noopener" class="drawer-pub-link-sec">📋 Brief</a>
  </div>
</div>
```

---

## Announcements Architecture

Announcements cover partnerships, feature interviews, publication releases, and research milestones — any news item that has public-facing significance beyond being listed as a research output.

### Page types and file naming

| Page | Filename | Purpose |
|------|----------|---------|
| Index | `announcements.html` | Lists all announcements, newest first, with a filter bar |
| Detail | `announcement-[slug].html` | Full story for a single announcement |

Slug convention: `announcement-[partner]-[type]` or `announcement-[topic]`. Examples: `announcement-maytree-interview.html`, `announcement-sshrc-grant-awarded.html`. Keep at repo root — do not use a subfolder unless/until the count exceeds ~15.

### Filter categories on the index page

Three filters + "All". A detail page's `data-type` on its `announce-card` must match one of these exactly:

| Filter value | Covers |
|------|---------|
| `partnership` | New partners, strategic partnership announcements, MOUs, featured interviews with partner organizations |
| `publication` | Major journal articles released, briefs launched, reports published, poster debuts |
| `event` | Conference presentations, media appearances, podcast features, webinars, talks |

### Announcement card (`announce-card`)

Two-column layout: left is a burgundy tile (date + partnership-type badge), right is the body (partner pills, title, blurb, read-more link). The whole card is a single `<a>` linking to the detail page.

```html
<a href="announcement-[slug].html" class="announce-card" data-type="[partnership|publication|event]">
  <div class="ac-tile">
    <div class="ac-date-block">
      <div class="ac-date-kicker">Published</div>
      <div class="ac-date">[Month DD, YYYY]<em>[Weekday]</em></div>
    </div>
    <div class="ac-badge-block">
      <div class="ac-badge">
        <span class="ac-badge-dot"></span>
        [Partnership|Publication|Event]
      </div>
      <div class="ac-stream">[Context line — e.g. "ENABLE Stream · MVPF Project"]</div>
    </div>
  </div>
  <div class="ac-body">
    <div class="ac-meta-row">
      <span class="ac-partner-pill">[Partner pill — e.g. "With Maytree"]</span>
      <span class="ac-partner-pill">[Optional second partner pill]</span>
      <span class="ac-project-pill">[Project shorthand — e.g. "MVPF"]</span>
    </div>
    <h3 class="ac-title">[Headline — sentence case, italicize names/titles with &lt;em&gt;]</h3>
    <p class="ac-blurb">[2–3 sentences, ~60–90 words. Same voice as output-blurb but reads like news rather than academic summary — what happened, why it matters, what the thing says.]</p>
    <span class="ac-read">Read the full announcement →</span>
  </div>
</a>
```

**Pill distinction:**
- `.ac-partner-pill` (rose/secondary-pale) — for partner attribution: "With Maytree", "Supported by Mitacs Accelerate"
- `.ac-project-pill` (gold/accent-pale) — for project tag: "MVPF", "Basic Income", "STR Calgary"

**Date format:** Full month name, no leading zero on day, comma, four-digit year. The weekday goes inside `<em>` for the small secondary line.

### Detail page structure

Use `announcement-maytree-interview.html` as the reference. Required sections in order:

1. **Hero** — breadcrumb (Home → Announcements → [Short Title]), partnership/publication/event badge, kicker line with project and date, title with italicized name in `<em>`, byline row with key partners.
2. **Lede** (Lora serif, larger) — one-paragraph summary.
3. **"What was published" / "What happened"** section — the facts of the announcement. If paraphrasing an external piece, paraphrase in INCLUSIECON voice — do not quote the external source at length (copyright). A single italic pull quote is fine if clearly attributed as paraphrase.
4. **"Why this partnership matters" / "Why this matters"** section — significance + partner strip (three-card grid: Research Lead · Strategic Partner · [third role]).
5. **Feature card** (optional) — for announcements centred on a person (e.g. featured researcher). Uses the `feature-researcher` component: burgundy gradient card, photo/initials circle, name + role + bio.
6. **"Key themes"** section (optional) — short synthesis of what the announcement surfaces.
7. **Large CTA link** (`cta-read`) — burgundy block linking out to the primary external resource.
8. **Related** — 3 items: project page, primary external asset, "All Announcements" link.

### Cross-linking from research project pages

When an announcement is tied to a research project, add it to that project's **Knowledge Mobilization** section as an `output-item` with the commentary icon (`💬 icon-commentary`). Link to both the external source (primary) and the INCLUSIECON announcement detail page (secondary) using `output-action-multi`:

```html
<div class="output-action">
  <div class="output-action-multi">
    <a href="[EXTERNAL URL]" target="_blank" rel="noopener" class="btn-read">Read ↗</a>
    <a href="announcement-[slug].html" class="btn-read-secondary">📣 Announcement</a>
  </div>
</div>
```

**Remember to update the stat count** at the top of the project page (`.stat-number` inside the `#knowledge-mobilization` `.stat-item`). If the page shows "2 Knowledge Mobilization" and you add an entry, change it to 3.

### SEO and sitemap

- Detail page canonical: `https://inclusiecon.ca/announcement-[slug].html`
- Add to `sitemap.xml` under a `<!-- Announcements -->` block, between the main pages and research program pages
- Index page priority: `0.85` (higher than research sub-pages because it aggregates); detail page priority: `0.7`; changefreq: `monthly` for index, `yearly` for detail pages once published

---

## Blurb Voice Guide

INCLUSIECON blurbs occupy a register **between academic and plain language**. The target reader is policy-literate — a researcher, public servant, journalist, or informed advocate who understands what a welfare analysis or microsimulation is, but doesn't need jargon explained and doesn't want to feel like they're reading an abstract. Think: accessible to a smart generalist, credible to a specialist.

**Voice rules:**

1. **Open with a strong active verb** in the third person: *Introduces, Develops, Argues, Applies, Examines, Documents, Proposes, Extends, Uses, Builds*. Never start with "This paper..." or "The authors..."

2. **Sentence 1: what the paper does.** Be precise and concrete. Name the framework, method, or empirical approach — but write it so a non-specialist can follow.

3. **Sentence 2: key mechanism or finding.** What does this add? What does it reveal? Include specific data points or results where they exist — they make blurbs credible without making them dense.

4. **Sentence 3 (optional, project page only):** A policy or practical payoff — what this enables or changes downstream.

5. **Length:**
   - `output-blurb` (project page): 2–3 sentences, ~60–100 words
   - `pub-blurb` (research hub): can run longer (3–4 sentences, up to 120 words) — these are the primary discovery card
   - `drawer-pub-blurb`: 1–2 sentences is fine

6. **Tone dos:** Confident but not breathless. Technically precise without being opaque. Em-dashes for parenthetical elaboration. Policy stakes visible but grounded in what the research actually shows.

7. **Tone don'ts:** No "groundbreaking," "important," "novel," "contributes to the literature." No passive voice in the opening. No "this paper examines." No academic throat-clearing. But also not punchy or journalistic — the register is measured, not sharp.

**Reference blurbs (gold standard):**

> *Introduces the MVPF-TAdmin framework — a welfare-based lens for evaluating tax administration reforms across three dimensions: fiscal efficiency, distributional equity, and legitimacy. Applied to Canada's Automatic Federal Benefits initiative as a proof of concept, showing how design quality determines whether a reform generates positive or negative social returns.*

> *Argues that Canada's capital budgeting framework misclassifies social spending as operating expenditure, systematically undervaluing programs that build human and social capacity. Applies MVPF logic to reframe transfers and supports as social investment — analytically more honest and politically more tractable than austerity framing.*

> *A new framework for inclusive cash transfer design integrating policy design, empirical economics, and systems thinking — moving beyond technocratic optimization to centre intersectionality, lived experience, and the structural conditions that make programs work or fail for the people they are meant to serve.*

---

## SEO Meta Tag Template

```html
<meta name="description" content="[One sentence, ~155 chars, plain language, what the page/paper is about]">
<meta name="keywords" content="[6–10 keywords: topic Canada, specific concept, related programs, author names]">
<link rel="canonical" href="https://inclusiecon.ca/[filename].html">
<meta property="og:type" content="article">
<meta property="og:title" content="[Page title] | INCLUSIECON">
<meta property="og:description" content="[Same as meta description]">
<meta property="og:url" content="https://inclusiecon.ca/[filename].html">
<meta property="og:site_name" content="INCLUSIECON">
<meta name="twitter:card" content="summary">
<meta name="twitter:title" content="[Page title] | INCLUSIECON">
<meta name="twitter:description" content="[Same as meta description]">
<meta name="robots" content="index, follow">
<meta name="author" content="Lindsay M. Tedds, Gillian Petit">
```

---

## Common Mistakes to Avoid

- ❌ Using "ENGAGE" — it's **ENABLE**
- ❌ Hardcoding hex colours — always use CSS variables
- ❌ Relative paths for PDFs — always use GitHub raw URLs
- ❌ Starting blurbs with "This paper..." or "The authors..."
- ❌ Linking to Selvia's name without the hyperlink to selviaarshad.com
- ❌ Writing "Lindsay Tedds" — always "Lindsay M. Tedds"
- ❌ Omitting `target="_blank" rel="noopener"` on external links
- ❌ Adding a new top-level section (like Announcements) to only some nav patterns — it must go into all three (main `ul/li`, sub-page `div/a`, brief `ul/li`-with-Home) across every file
- ❌ Adding a Knowledge Mobilization entry to a research project page without updating the `.stat-number` count in the hero stats block
- ❌ Quoting external publications (e.g. Maytree, IRPP, government reports) at length on announcement pages — paraphrase in INCLUSIECON voice to stay copyright-clean
- ❌ Including `edia.html` in nav or footer — the EDIA page is referenced in some drafts but is not part of the live top-nav structure

---

## Research Areas Quick Reference

For full output lists and funder details, see `references/research-areas.md`.

| Page | Stream | Key Funders |
|------|--------|-------------|
| research-basic-income.html | FACT + ENABLE | BC Expert Panel, various |
| research-mvpf.html | ENABLE | Maytree (strategic partner), Mitacs Accelerate |
| research-intersectionality.html | FACT + ENABLE | — |
| research-str-calgary.html | FACT | City of Calgary CIF, AREF (pre-project only) |
| research-property-tax.html | FACT | — |
