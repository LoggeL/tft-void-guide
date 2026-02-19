Update the positioning grid section in index.html:

## CHANGE 1: Horizontal Mirror
Flip all champion positions horizontally. Column 1 becomes column 7, column 7 becomes column 1, column 2 becomes column 6, etc. (mirror across center axis).

Current positions → mirrored:
### LVL 6:
- Cho'Gath: front col 2 → front col 6
- Rek'Sai: front col 4 → front col 4 (center, stays)
- Kog'Maw: back col 3 → back col 5
- Malzahar: back col 5 → back col 3

### LVL 8:
- Cho'Gath: front col 1 → front col 7
- Rift Herald: front col 4 → front col 4
- Rek'Sai: front col 6 → front col 2
- Bel'Veth: row2 col 3 → row2 col 5
- Kai'Sa: back col 4 → back col 4
- Kog'Maw: back col 2 → back col 6
- Malzahar: back col 6 → back col 2

### LVL 9:
- Cho'Gath: front col 1 → front col 7
- Rift Herald: front col 3 → front col 5
- Volibear: front col 4 → front col 4
- Rek'Sai: front col 5 → front col 3
- Baron: front col 7 → front col 1
- Bel'Veth: row2 col 1 → row2 col 7
- Kai'Sa: back col 4 → back col 4
- Kog'Maw: back col 2 → back col 6
- Malzahar: back col 6 → back col 2

### LVL 10:
- Cho'Gath: front col 1 → front col 7
- Rift Herald: front col 3 → front col 5
- Baron: front col 4 → front col 4
- Volibear: front col 5 → front col 3
- Rek'Sai: front col 6 → front col 2
- Bel'Veth: row2 col 1 → row2 col 7
- Kai'Sa: back col 4 → back col 4
- Kog'Maw: back col 2 → back col 6
- Malzahar: back col 6 → back col 2

---

## CHANGE 2: Hex Grid Layout (TFT Style)

Replace the current rectangular CSS grid with a proper TFT-style hex grid.

### TFT Hex Grid Rules:
- TFT board = 4 rows × 7 columns
- Odd rows (1, 3) are NOT offset
- Even rows (2, 4) are offset by half a hex width to the RIGHT
- Row 1 = BOTTOM (frontline, closest to enemies)
- Row 4 = TOP (backline)
- Each hex = flat-top hexagon OR just use circles with correct offset (simpler)

### Implementation using CSS (offset circles — simpler than SVG hexagons):
Use a relative positioned container. Each row is a flex row. Even rows get margin-left: half hex size.

```css
.hex-board {
  display: flex;
  flex-direction: column-reverse; /* row 1 at bottom */
  gap: 4px;
  padding: 16px;
}
.hex-row {
  display: flex;
  gap: 6px;
}
.hex-row.offset {
  margin-left: 26px; /* half of hex width + gap */
}
.hex-cell {
  width: 52px;
  height: 52px;
  border-radius: 50%;
  /* hex look: use clip-path for real hexagon */
  clip-path: polygon(50% 0%, 100% 25%, 100% 75%, 50% 100%, 0% 75%, 0% 25%);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  position: relative;
}
```

### Real hex shape using clip-path:
clip-path: polygon(50% 0%, 100% 25%, 100% 75%, 50% 100%, 0% 75%, 0% 25%)

This gives a proper hexagon shape (pointy-top style, like TFT).

### Hex cell states:
- Empty hex: background: rgba(255,255,255,0.05), border via outline trick or wrapper div
- Occupied hex with champion: show champion portrait as background-image (cover), with a colored overlay/border based on role
  - Tank (blue): border color #06b6d4
  - Carry (purple): border color #8b5cf6
  - Flex (gray): border color #6b7280
  - Baron special (gold): border color #f59e0b, glow effect

For the border on clip-path hexes, use a wrapper trick:
```html
<div class="hex-wrapper tank">  <!-- wrapper adds colored background -->
  <div class="hex-cell">
    <img src="..." />
    <span class="hex-label">CHO</span>
  </div>
</div>
```
The wrapper has the same clip-path but is 4px larger, positioned behind with the border color as background.

### Champion portrait as hex background:
Instead of <img> inside hex, use background-image: url(...) on the hex cell itself (background-size: cover, background-position: center). Put the label below the hex (outside the clip-path so it's visible).

### Label positioning:
Put champion abbreviation BELOW each hex cell (in a separate <span> outside the clip-path wrapper), small text, white, centered.

### Row offset logic (which rows get offset):
In TFT, rows 2 and 4 (counting from bottom) are offset. Since we use flex-direction: column-reverse:
- The HTML order is row4, row3, row2, row1
- rows 2 and 4 from bottom = row2 and row4 in game = rows at index 1 and 3 in column-reverse
- Apply class "offset" to these rows

### Mobile:
Wrap the entire board in overflow-x: auto container. Min-width: 420px for the board itself.

---

## Keep everything else intact.
Only update the positioning grid HTML/CSS/JS. Keep all other sections unchanged.

After updating:
1. git add index.html
2. git commit -m "feat: hex grid positioning with TFT-style offset rows"
3. git push origin master

When done:
openclaw system event --text "Done: Hex grid positioning pushed" --mode now
