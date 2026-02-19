Update index.html with these 3 changes. ALL image URLs below are verified 200 OK — use them EXACTLY as written.

---

## CHANGE 1: Add items for Baron Nashor, Rift Herald, Bel'Veth + Mutation Icons

CDN base for items: https://raw.communitydragon.org/latest/plugins/rcp-be-lol-game-data/global/default/assets/maps/tft/icons/items/hexcore/

### Baron Nashor items (AD/bruiser carry):
- Infinity Edge:     https://raw.communitydragon.org/latest/plugins/rcp-be-lol-game-data/global/default/assets/maps/tft/icons/items/hexcore/tft_item_infinityedge.tft_set13.png
- Bloodthirster:     https://raw.communitydragon.org/latest/plugins/rcp-be-lol-game-data/global/default/assets/maps/tft/icons/items/hexcore/tft_item_bloodthirster.tft_set13.png
- Sterak's Gage:     https://raw.communitydragon.org/latest/plugins/rcp-be-lol-game-data/global/default/assets/maps/tft/icons/items/hexcore/tft_item_steraksgage.tft_set13.png

### Rift Herald items (tank):
- Warmog's Armor:       https://raw.communitydragon.org/latest/plugins/rcp-be-lol-game-data/global/default/assets/maps/tft/icons/items/hexcore/tft_item_warmogsarmor.tft_set13.png
- Gargoyle Stoneplate:  https://raw.communitydragon.org/latest/plugins/rcp-be-lol-game-data/global/default/assets/maps/tft/icons/items/hexcore/tft_item_gargoylestoneplate.tft_set13.png
- Ionic Spark:          https://raw.communitydragon.org/latest/plugins/rcp-be-lol-game-data/global/default/assets/maps/tft/icons/items/hexcore/tft_item_ionicspark.tft_set13.png

### Bel'Veth items (slayer carry):
- Infinity Edge:    https://raw.communitydragon.org/latest/plugins/rcp-be-lol-game-data/global/default/assets/maps/tft/icons/items/hexcore/tft_item_infinityedge.tft_set13.png
- Titan's Resolve:  https://raw.communitydragon.org/latest/plugins/rcp-be-lol-game-data/global/default/assets/maps/tft/icons/items/hexcore/tft_item_titansresolve.tft_set13.png
- Last Whisper:     https://raw.communitydragon.org/latest/plugins/rcp-be-lol-game-data/global/default/assets/maps/tft/icons/items/hexcore/tft_item_lastwhisper.tft_set13.png

### Void Mutation icons (replace or enhance the existing mutations list for Kai'Sa section + add Rift Herald mutation):
- Spitter Spines:      https://raw.communitydragon.org/latest/plugins/rcp-be-lol-game-data/global/default/assets/maps/tft/icons/items/hexcore/tft16_voidmutation_spitterspines.tft_set16.png
- Leeching Nucleus:    https://raw.communitydragon.org/latest/plugins/rcp-be-lol-game-data/global/default/assets/maps/tft/icons/items/hexcore/tft16_voidmutation_leechingnucleus.tft_set16.png
- Adrenaline Modules:  https://raw.communitydragon.org/latest/plugins/rcp-be-lol-game-data/global/default/assets/maps/tft/icons/items/hexcore/tft16_voidmutation_adrenalinemodules.tft_set16.png
- Iron Carapace:       https://raw.communitydragon.org/latest/plugins/rcp-be-lol-game-data/global/default/assets/maps/tft/icons/items/hexcore/tft16_voidmutation_ironcarapace.tft_set16.png

Show mutations per unit in the items section:
- Kai'Sa mutations (priority): Spitter Spines (S) → Leeching Nucleus (A) → Adrenaline Modules (B)
- Rift Herald mutation: Iron Carapace
- Baron Nashor mutation: Spitter Spines (best available)

---

## CHANGE 2: Add Positioning Grid Section

Add a new section AFTER the stage guide section (before items section) titled "POSITIONING".

The TFT board is 4 rows × 7 columns. Show 4 board states:

### Board at Level 6 (Early Void):
```
Row 4 (back):   [ ] [ ] [KOG] [ ] [MAL] [ ] [ ]
Row 3:          [ ] [ ] [ ] [ ] [ ] [ ] [ ]
Row 2:          [ ] [ ] [ ] [ ] [ ] [ ] [ ]
Row 1 (front):  [ ] [CHO] [ ] [REK] [ ] [ ] [ ]
```
Units: Cho'Gath (front col 2), Rek'Sai (front col 4), Kog'Maw (back col 3), Malzahar (back col 5)

### Board at Level 8:
```
Row 4 (back):   [ ] [KOG] [ ] [KAI] [ ] [MAL] [ ]
Row 3:          [ ] [ ] [ ] [ ] [ ] [ ] [ ]
Row 2:          [ ] [ ] [BEL] [ ] [ ] [ ] [ ]
Row 1 (front):  [CHO] [ ] [ ] [RFT] [ ] [REK] [ ]
```
Units: Cho'Gath (front col 1), Rift Herald (front col 4), Rek'Sai (front col 6), Bel'Veth (mid col 3), Kai'Sa (back col 4), Kog'Maw (back col 2), Malzahar (back col 6)

### Board at Level 9:
```
Row 4 (back):   [ ] [KOG] [ ] [KAI] [ ] [MAL] [ ]
Row 3:          [ ] [ ] [ ] [ ] [ ] [ ] [ ]
Row 2:          [BEL] [ ] [ ] [ ] [ ] [ ] [ ]
Row 1 (front):  [CHO] [ ] [RFT] [VOL] [REK] [ ] [BAR]
```
Units: Cho'Gath (front col 1), Rift Herald (front col 3), Volibear (front col 4), Rek'Sai (front col 5), Baron Nashor (front col 7), Bel'Veth (row 2 col 1), Kai'Sa (back col 4), Kog'Maw (back col 2), Malzahar (back col 6)

### Board at Level 10 (Full Cap):
```
Row 4 (back):   [ ] [KOG] [ ] [KAI] [ ] [MAL] [ ]
Row 3:          [ ] [ ] [ ] [ ] [ ] [ ] [ ]
Row 2:          [BEL] [ ] [ ] [ ] [ ] [ ] [ ]
Row 1 (front):  [CHO] [ ] [RFT] [BAR] [VOL] [REK] [ ]
```
Units: Cho'Gath (front col 1), Rift Herald (front col 3), Baron Nashor (front col 4 — center!), Volibear (front col 5), Rek'Sai (front col 6), Bel'Veth (row 2 col 1), Kai'Sa (back col 4), Kog'Maw (back col 2), Malzahar (back col 6)
Note: "Baron at center front — charges into the enemy backline!"

### How to render the positioning grid in HTML/CSS:
- 4 tabs/buttons to switch between Level 6, 8, 9, 10 boards (tab style, purple/void themed)
- Each board: CSS grid, 7 columns × 4 rows
- Occupied hexes: show small champion portrait (40x40px circular, same CDN URLs as champion section) + abbreviation label below
- Empty hexes: dark semi-transparent circle with subtle border
- Hex style: rounded circles (border-radius: 50%), slight 3D feel with box-shadow
- Active tab highlights in purple
- Board background: dark with subtle grid pattern
- Label below each champion icon (abbreviated: CHO, REK, KOG, etc.)
- Color-code by role: tanks = blue-ish border, carries = purple border, flex = gray border

### Tab labels:
- "LVL 6" — Early
- "LVL 8" — Stable
- "LVL 9" — Power Spike
- "LVL 10" — Full Cap

Use JS to switch between boards (hide/show divs with display:none / display:grid).
Keep design consistent with existing glassmorphism dark theme.

---

## IMPLEMENTATION NOTES
- Keep ALL existing content and styles intact
- Only ADD new content — the items section, mutation icons, and positioning section
- For items: find the existing champion item sections for Kai'Sa, Baron, Rift Herald, Bel'Veth and add/update their item img tags
- The mutation icons should replace text-only mutation labels with icon + text
- Mobile: positioning grid should scroll horizontally on small screens (overflow-x: auto)

---

## After updating:
1. git add index.html
2. git commit -m "feat: add positioning grid, fix items for Baron/Herald/Belveth, add mutation icons"
3. git push origin master

When done:
openclaw system event --text "Done: Positioning grid + item fixes pushed to TFT guide" --mode now
