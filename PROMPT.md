Build an EPIC, premium TFT Set 16 Void Comp guide website. Single HTML file (index.html) — no build tools, no frameworks, just pure HTML/CSS/JS.

## CONTENT: TFT Set 16 Void Comp Guide

### Champions (in order of acquisition):
Early game: Kog'Maw, Malzahar, Rek'Sai
Mid game: Cho'Gath, Rift Herald, Kai'Sa, Bel'Veth
Late game: Volibear (flex: Swain / Shyvana)
Cap (Lvl 10): Baron Nashor

### Traits:
- 9x Void (main)
- 2x Bruiser
- Longshot

### Leveling Guide:
- Lvl 4: Level up if you have upgrades + good item
- Lvl 5: Always, unless on 3x loss streak
- Lvl 6: On 4+ winstreak OR can stay above 40g
- Lvl 7: If you can stay above 30g
- Lvl 8: Roll for Kai'Sa 2-star + Rift Herald 2-star (do NOT go below 10g)
- Lvl 9: High HP → wait until stage 5-5 | Medium HP → roll 20g first | Low HP → go ASAP
- Lvl 10: Only when carry is itemized + upgraded → get Baron Nashor → transfer items + best Void mutation

### Early Game (Stage 2-3):
Slam items aggressively. Play for winstreak. Have 4 Void by 2-5 to unlock Rift Herald.

### Stage 4:
Roll on level 8 for Kai'Sa 2-star + Rift Herald 2-star. Push to 9. Flex with Swain or Shyvana.

### Stage 5+:
9 Void + Bruiser (Wukong → Volibear). Once Baron online: transfer items + best Void mutation.

### Items:
Kai'Sa: AP items preferred
Mutations (Kai'Sa): Splitter Spines → Leeching Nucleus → Adrenaline Modules

### Win Condition:
Push to Level 10 for Baron Nashor. Baron gets the best Void mutation.

---

## DESIGN REQUIREMENTS

### Aesthetic: "Classified Leak meets Premium Game Guide"
- Dark theme: Deep dark background (#080b12 or similar deep navy-black)
- Void color palette: Purple/violet (#8b5cf6, #a78bfa), cyan accents (#06b6d4), dark red danger tones (#ef4444) for warnings
- Leak-style elements: Classified watermarks, "INTERNAL USE ONLY" stamps, redacted text bars that hover to reveal, glitch effects
- Premium finish: Glassmorphism cards, subtle gradients, professional typography

### Typography:
- Use Google Fonts: "Rajdhani" or "Orbitron" for headings (futuristic/game feel)
- "Inter" or "Roboto" for body text
- Monospace font for data elements (stats, numbers)

### Layout:
1. Hero section: Full-viewport dark hero with animated Void particle background (canvas particles), "VOID COMP GUIDE" in massive glitchy text, "SET 16 | PATCH 16.4" subtitle, a "CLASSIFIED" red stamp overlay, pulsing scroll CTA
2. Champions section: Grid of champion cards with: name, star rating, cost badge (colored: 1=gray,2=green,3=blue,4=purple,5=gold), role tag (Early/Mid/Late/Cap), hover animation (lift + purple glow)
3. Leveling Timeline: Vertical timeline with each level as a node, level number in circle, condition text, color code (green/yellow/red), animated connecting line
4. Stage-by-Stage Guide: 3 cards (Stage 2-3 / Stage 4 / Stage 5+) with stage badge, icon, key actions as bullet points
5. Items & Mutations: Card showing Kai'Sa with item priority, mutation priority list with rank badges (S/A/B)
6. Win Condition Banner: Full-width "PUSH TO LEVEL 10" CTA with Baron Nashor theme
7. Footer: "Guide by Rowdy AI • TFT Set 16 • Patch 16.4"

### Animations:
- Particle background: Floating purple/cyan dots in hero (canvas requestAnimationFrame)
- Glitch text effect: Hero title has CSS glitch animation
- Scroll reveal: Sections fade/slide in on scroll (IntersectionObserver)
- Card hover: lift (translateY(-8px)), purple glow box-shadow, scale 1.02
- Level timeline fill: Connecting line animates on scroll
- Classified stamp: Appears with rotation bounce on page load
- Scan line overlay: Subtle horizontal scan lines on hero (CRT feel)
- Glassmorphism cards: backdrop-filter blur, semi-transparent backgrounds, gradient borders (1px purple to cyan)

### Mobile responsive: Stack columns, horizontal scroll for champions on small screens.

---

## TECHNICAL
- Single index.html file (inline ALL CSS and JS — only Google Fonts from CDN)
- No build step
- Works from file:// and GitHub Pages
- Use will-change and transform for smooth animations

---

After building index.html, also create:
- README.md (short description with screenshot placeholder)
- .nojekyll (empty file for GitHub Pages)

Then run these commands:
1. git add -A
2. git commit -m "feat: epic TFT Set 16 Void Comp guide"
3. gh repo create LoggeL/tft-void-guide --public --source=. --remote=origin --push
4. gh api repos/LoggeL/tft-void-guide/pages --method POST -f source.branch=master -f source.path=/

When completely finished, run:
openclaw system event --text "Done: TFT Void Guide live! https://loggel.github.io/tft-void-guide" --mode now
