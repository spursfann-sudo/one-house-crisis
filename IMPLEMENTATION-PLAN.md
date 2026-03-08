# Plan: Crisis Housing Presentation Improvements

## Context
The One House Project has a single-page HTML presentation (`one-house-crisis-intervention.html`) used to pitch their crisis housing model to potential partners. The presentation has 17 slides across 7 chapters with embedded CSS/JS. Three issues need fixing now, and two items (brand images, content enrichment from additional artifacts) will be addressed after the user adds files.

## What We're Doing Now

### 1. Improve Sidebar Navigation
**Problem:** The sidebar only shows 7 chapter-level buttons. Slides within a chapter (e.g., "The Problem" has 4 slides) are only reachable via keyboard arrows or swipe — not discoverable.

**Solution:**
- Add `data-title` attributes to each of the 17 `<div class="slide">` elements with short descriptive names
- Rewrite the JS nav builder to render a two-level hierarchy: chapter headings with individual slide links nested underneath
- Add CSS for the nested nav: chapter labels as non-clickable group headers, slide links indented beneath, active slide highlighted, subtle visual grouping
- Update `update()` to highlight the active slide (not just the active chapter)
- Keep chapter color dots on the group headers

**Slide titles to add:**
| # | Chapter | Title |
|---|---------|-------|
| 1 | The Problem | Title |
| 2 | The Problem | The Gap |
| 3 | The Problem | Cost of Inaction |
| 4 | The Problem | Root Cause |
| 5 | The Model | Coordination Layer |
| 6 | The Model | Core Principles |
| 7 | The Continuum | Overview |
| 8 | The Continuum | Stages 1 & 2 |
| 9 | The Continuum | Stages 3 & 4 |
| 10 | Partner Network | Four Roles |
| 11 | Partner Network | Role Details |
| 12 | Partner Network | The Opportunity |
| 13 | How It Works | Five Steps |
| 14 | How It Works | What We Provide |
| 15 | Sustainability | Financial Model |
| 16 | Next Steps | Leadership |
| 17 | Next Steps | Raise Your Hand |

**File:** `one-house-crisis-intervention.html` — lines 80-137 (sidebar CSS), lines 816-1301 (slide HTML), lines 1304-1408 (JS)

### 2. Create Partner Intake Form Page (UI Only)
**Problem:** No way for interested partners to take the next step after viewing the presentation.

**Solution:** Create `intake-form.html` — a standalone page styled consistently with the presentation brand. Form fields (no submission wiring):

- **Organization Info:** Name, type (church/nonprofit/business/government/individual), city/state
- **Contact:** Name, email, phone
- **Interest:** Which partner role(s) interest you? (checkboxes: Sponsor, Operator, Facility, Service Provider)
- **Housing Stage:** Which stage(s)? (checkboxes: Emergency Shelter, Recovery Center, Bridge Housing, Launch Pad, Not Sure)
- **Population:** Who would you like to serve? (free text)
- **What do you bring?** (free text — funding, property, operational experience, clinical expertise, etc.)
- **Anything else?** (free text)
- Submit button (styled but non-functional, with a note: "Submission coming soon — for now, email us at [placeholder]")

**Styling:** Same Google Fonts import, same CSS variables, brand logo at top, clean form layout, mobile-friendly. Back-link to the presentation.

**File:** New file `intake-form.html`

### 3. Update Final CTA Slide
**Problem:** The last slide ("Ready to raise your hand?") only lists website/social/donation links — no actionable next step for partners.

**Solution:**
- Add a prominent "Become a Partner" button linking to `intake-form.html`
- Keep existing links but make them secondary
- Style the button with brand blue, hover state, and clear visual hierarchy

**File:** `one-house-crisis-intervention.html` — lines 1281-1300 (slide 17 HTML), add button CSS

### 4. Prepare for Brand Assets (Deferred)
The user will add image files (logo, team headshots) to the repo. No changes now — but the structure will be ready:
- Team avatars currently use initials in colored circles — easy to swap to `<img>` tags
- Logo uses CSS shapes — easy to swap to an `<img>` or inline SVG

### 5. Add Missing Fuzzy Bubbles Font
**Problem:** The brand system specifies Fuzzy Bubbles for accents, but it's not imported.

**Solution:** Add Fuzzy Bubbles to the Google Fonts import URL. Add a CSS utility class. (We won't apply it broadly until the user confirms where they want it, but it will be available.)

**File:** `one-house-crisis-intervention.html` — line 7 (font import), CSS section

## Deferred: Brand Alignment Review
The website review of https://onehouseproject.com was attempted but did not complete due to a rate limit. Once the user adds their brand image files and additional artifacts to the repo, we will:
1. Review the live site for brand alignment (colors, typography, layout patterns, CTAs, imagery)
2. Wire in the actual logo and team headshot images
3. Enrich slide content based on the additional artifacts provided
4. Apply any brand alignment fixes identified from the website review

## Verification
1. Open `one-house-crisis-intervention.html` in a browser
2. Confirm all 17 slides are individually clickable from the sidebar
3. Confirm sidebar highlights track the current slide when using keyboard nav
4. Click "Become a Partner" on the final slide — should open `intake-form.html`
5. Confirm intake form renders cleanly with all fields, brand styling, and back-link
6. Test keyboard navigation still works (arrow keys, space)
7. Test touch/swipe still works
