Update the existing index.html in this directory to add images to champion cards and items.

## Champion Images
Use Riot's Data Dragon CDN for champion portrait icons. Current patch: check https://ddragon.leagueoflegends.com/api/versions.json and use the first (latest) version.

URL pattern: https://ddragon.leagueoflegends.com/cdn/{VERSION}/img/champion/{Name}.png

Champions in the guide and their exact Data Dragon names:
- Kog'Maw → KogMaw
- Malzahar → Malzahar
- Rek'Sai → RekSai
- Cho'Gath → Chogath
- Kai'Sa → Kaisa
- Bel'Veth → Belveth
- Volibear → Volibear
- Swain → Swain
- Shyvana → Shyvana

For "Rift Herald" and "Baron Nashor" — these are Void monsters, not standard champions. Use these Community Dragon URLs instead:
- Rift Herald: https://raw.communitydragon.org/latest/game/assets/ux/tft/championsplashes/tft16_riftheraldboss.tft_set16.png
  Fallback if not found: use a purple void circle with "RH" text via CSS (no broken img)
- Baron Nashor: https://raw.communitydragon.org/latest/game/assets/ux/tft/championsplashes/tft16_baron.tft_set16.png
  Fallback: use a gold void circle with "BN" text via CSS

## How to add images to champion cards
Find the champion card elements in the HTML. Each card should have an img element added at the top of the card:
- Size: 64x64px (or 72x72px) circular/rounded image
- Style: border-radius: 50%, border: 2px solid matching cost color, object-fit: cover
- Add onerror handler to hide broken images gracefully: onerror="this.style.display='none'"
- Position: centered at top of card, above the name

## TFT Item Images
For TFT-specific items, use Community Dragon:
URL pattern: https://raw.communitydragon.org/latest/plugins/rcp-be-lol-game-data/global/default/assets/items/icons2d/

The items for Kai'Sa in TFT Set 16 are typically AP items like:
- Rabadon's Deathcap → search community dragon for "rabadons" 
- Jeweled Gauntlet → search for "jeweled"
- Blue Buff → standard TFT item

Actually, for TFT items the CDN path is:
https://raw.communitydragon.org/latest/plugins/rcp-be-lol-game-data/global/default/assets/items/icons2d/{itemname}.png

For items section, add small 40x40px item icons. If you can't find exact TFT item icons, use the standard LoL item icons from Data Dragon:
https://ddragon.leagueoflegends.com/cdn/{VERSION}/img/item/{itemId}.png

Key items to show (these are standard LoL item IDs that correspond to TFT components):
- Rabadon's Deathcap: 3089
- Jeweled Gauntlet: use 3135 (Void Staff) as placeholder  
- Blue Buff: use 3003 (Archangel's) as placeholder
- Giant Slayer: 3036
- Shadowflame: 4645

Just pick 3 good-looking AP item images to put on Kai'Sa's card.

## Implementation notes
- Fetch the version dynamically using JS fetch on page load, OR just hardcode "15.4.1" as the version (check if it works first)
- Add loading="lazy" to all images
- Add onerror="this.style.display='none'" to all images so broken ones disappear cleanly
- Keep all existing styles and animations intact — only ADD images, don't break anything

## After updating index.html:
1. git add index.html
2. git commit -m "feat: add champion portraits and item icons"
3. git push origin master

When done, run:
openclaw system event --text "Done: Champion images added to TFT guide" --mode now
