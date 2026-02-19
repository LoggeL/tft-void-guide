# Task: Create TFT Comp Hub / Landing Page

## Goal
Create a new hub/landing page that acts as the entry point for a TFT Set 16 comp guide collection.

## File Structure Changes
1. Move `index.html` → `void/index.html` (create the `void/` subfolder)
2. Create new `index.html` at the root — this is the hub page
3. Copy `.nojekyll` to root (should already be there)
4. Update the back-link in `void/index.html` (if any) to link back to `../index.html`

## Hub Page (`index.html`) Requirements

### Visual Style
- Same dark void/space aesthetic as the existing comp guide (matching CSS variables, fonts, colors)
- Background: deep space dark (`#0a0a12`) with subtle particle/star field effect (same JS as existing page)
- Use the same Google Fonts (Rajdhani, Orbitron) already linked in the existing index.html
- Glassmorphism cards with `backdrop-filter: blur`
- Purple/cyan/gold accent colors matching existing guide

### Header
- Title: **"TFT SET 16 — COMP GUIDE"** in Orbitron font, glitch effect (same as existing)
- Subtitle: "Choose your battlefield. Master your comp."
- A small "PATCH 16.4" badge

### Comp Cards Grid
Display a responsive grid (2-3 columns on desktop, 1 on mobile) of comp selection cards.

#### Card 1: Void Comp (ACTIVE)
- Title: **"VOID"** with trait icon glow
- Tier badge: **A-TIER** (gold/amber)
- Show 4-5 champion portraits in a row (use the existing CDN URLs):
  - Kog'Maw: `https://raw.communitydragon.org/latest/game/assets/characters/tft16_kogmaw/hud/tft16_kogmaw_square.tft_set16.png`
  - Kai'Sa: `https://raw.communitydragon.org/latest/game/assets/characters/tft16_kaisa/hud/tft16_kaisa_square.tft_set16.png`
  - Malzahar: `https://raw.communitydragon.org/latest/game/assets/characters/tft16_malzahar/hud/tft16_malzahar_square.tft_set16.png`
  - Baron Nashor: `https://raw.communitydragon.org/latest/game/assets/characters/tft16_baronnashor/hud/tft16_baronnashor_square.tft_set16.png`
  - Bel'Veth: `https://raw.communitydragon.org/latest/game/assets/characters/tft16_belveth/hud/tft16_belveth_square.tft_set16.png`
- Tags: `FAST 9` `VOID` `AP/TANK`
- Short desc: "Level 10 Baron Nashor win condition. Kog'Maw → Kai'Sa item transfer via Longshot."
- **"VIEW GUIDE →"** button that links to `./void/index.html`
- Card has purple glow border, NOT greyed out

#### Cards 2, 3, 4 (COMING SOON placeholders)
Make 3 placeholder cards with the "COMING SOON" state:

Card 2:
- Title: **"???"** 
- Greyed out, blurred/locked aesthetic
- Show 5 silhouette/placeholder champion slots (dark grey boxes with `?` inside)
- Tags: `COMING SOON`
- A "LOCKED 🔒" button (disabled, not clickable)
- Subtle scanline overlay on the card

Card 3: same as Card 2

Card 4: same as Card 2

### Footer
- "More comps coming soon — stay tuned"
- Link back to the Void guide

### Animations
- Cards have hover lift effect (translateY(-8px), glow intensifies)
- The active Void card pulses subtly
- Coming soon cards have a subtle shimmer/scanline animation
- On page load, cards fade in with stagger (same reveal pattern as existing page)

## Technical Notes
- Single file `index.html` — no build tools, no external JS libraries
- Inline all CSS and JS
- Must work with GitHub Pages (static files only)
- Copy the particle JS from the existing `void/index.html` for the background
- The `void/index.html` should have a "← Back to Hub" link in the top-left corner

## After Building
Run these git commands:
```bash
cd /home/fedora/projects/tft-void-guide
git add -A
git commit -m "feat: add comp hub landing page, move void guide to /void/"
git push origin master
```

Then output: "DONE: hub deployed"
