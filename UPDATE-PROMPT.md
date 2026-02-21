# Prompt — Update Interactive User Journey Map

Open this project in VS Code Claude at:
`/Users/bahubalishete/Projects/KYN AI VS Code/sweatand-tonic-member-py0cut/docs/user-flows/deploy-to-vercel`

---

## Prompt

```
I need to update the interactive user journey map at `public/index.html`. The user flow documentation has been updated to be in sync with the current codebase. The HTML needs to reflect these updates.

## What This Is

A single-file interactive user journey map (HTML + inline CSS + inline JS) deployed to Vercel. It has:
- 6 lifecycle phases as columns: Activate → Onboard → Engage → Reflect → Optimize → Retain
- 7 rows: Touchpoints, User Actions, Emotional Arc, Pain Points, Opportunities, Backend/APIs, Personas
- Clickable touchpoint cards that open detail overlay modals
- Persona filter buttons (All / New Member / Active Member / Power User)
- Stats bar with key numbers
- Dark theme with S&T brand colors

## CRITICAL RULES

1. **Keep the EXACT same visual design** — do NOT change any CSS, layout structure, color variables, animations, or interactions
2. **Keep the EXACT same HTML structure** — same grid layout, same class names, same component patterns
3. **Keep the EXACT same JavaScript** — same showDetail/closeDetail/filterPersona functions, same event handlers
4. **ONLY update the DATA CONTENT** — touchpoint names, descriptions, user actions, pain points, opportunities, APIs, detail modal data, stats bar numbers
5. The output must remain a **single self-contained HTML file** with all CSS and JS inline
6. Read ALL 10 source-of-truth flow docs BEFORE making any changes (listed below)

## Source of Truth

Read these files in order. They are the ONLY source of truth for what goes in the journey map. The current `public/index.html` may have outdated content — replace it with what these docs say:

```
docs/user-flows/00-master-flow-map.md     — Overall architecture, screen counts, nav model
docs/user-flows/01-authentication-flow.md  — Flow 1: Activate phase
docs/user-flows/02-onboarding-intake-flow.md — Flow 2: Onboard phase
docs/user-flows/03-home-screen-flow.md     — Flow 3: Engage phase (home)
docs/user-flows/04-schedule-booking-flow.md — Flow 4: Engage phase (schedule/booking)
docs/user-flows/05-weekly-checkin-flow.md   — Flow 5: Reflect + Optimize phases
docs/user-flows/06-spot-selection-flow.md   — Flow 6: Spans Onboard + Engage
docs/user-flows/07-profile-settings-flow.md — Flow 7: Retain phase
docs/user-flows/08-post-class-checkin-flow.md — Flow 8: Reflect phase
docs/user-flows/09-magic-flow-goal-alignment.md — Flow 9: Optimize phase
```

All flow docs are relative to the project root at:
`/Users/bahubalishete/Projects/KYN AI VS Code/sweatand-tonic-member-py0cut/`

## What to Update

### 1. Stats Bar
Update the numbers from `00-master-flow-map.md`:
- Total flows, total screens, studio layouts, pillars, API integrations, exit points, hero states
- If any numbers changed in the updated docs, reflect them

### 2. Touchpoints Row
For each phase column, update touchpoint cards:
- Screen names and routes (verify against each flow doc)
- Flow tags (F1, F2, etc.)
- State callouts (decision branches, time windows, etc.)
- Add any NEW touchpoints that appear in updated docs
- Remove any touchpoints that no longer exist

### 3. User Actions Row
Update user actions per phase from the flow docs. Each action should be a concise verb phrase.

### 4. Emotional Arc Row
Keep the same 2-emotion-per-phase pattern. Update the quotes/labels if the flow docs reveal new emotional states or if the existing ones no longer match the current flow (e.g., if a pain point was fixed).

### 5. Pain Points Row
Update from each flow doc's friction points, confusion areas, drop-off risks. Keep the ▲ icon pattern.

### 6. Opportunities Row
Update from each flow doc. Keep the ★ icon pattern. If new features were added that resolve previous opportunities, replace with new ones.

### 7. Backend/APIs Row
Update API names from each flow doc. Use the KPI badge pattern. Verify all API call names match current docs.

### 8. Personas Row
Update which personas engage at each phase. Keep the tag pattern.

### 9. Detail Overlay Data (JavaScript `details` object)
This is the most important update. The `details` constant in the `<script>` block contains drill-down data for every clickable touchpoint. For each touchpoint, update:
- `title` — screen name
- `phase` — phase name
- `flow` — flow label
- `screen` — route path(s)
- `description` — 1-2 sentence summary from flow doc
- `inputs` — what the user provides/interacts with
- `outputs` — what happens as a result
- `decisions` — key branching logic
- `errors` — error states and handling
- `apis` — API calls made

Add new detail entries for any new touchpoints. Remove entries for touchpoints that no longer exist.

## How to Work

1. Read ALL 10 flow docs first — understand the full picture
2. Read the current `public/index.html` to understand the existing structure
3. Diff the flow docs against the current HTML content to identify what changed
4. Update ONLY the data content — do not touch CSS, layout, or JS logic
5. Write the complete updated `public/index.html`
6. Verify: every touchpoint in the HTML should trace back to a specific flow doc

## Deploy

After updating, deploy with:
```bash
cd /Users/bahubalishete/Projects/KYN AI VS Code/sweatand-tonic-member-py0cut/docs/user-flows/deploy-to-vercel
npx vercel --prod
```
```
