Fix ALL images in index.html. Replace every existing champion img src and item img src with the EXACT correct URLs listed below. Do NOT guess or invent paths.

## CHAMPION IMAGES — Replace all champion img src attributes

Base pattern: https://raw.communitydragon.org/latest/game/assets/characters/tft16_{CHAMP}/hud/tft16_{CHAMP}_square.tft_set16.png

Exact URLs (copy verbatim):
- Kog'Maw:    https://raw.communitydragon.org/latest/game/assets/characters/tft16_kogmaw/hud/tft16_kogmaw_square.tft_set16.png
- Malzahar:   https://raw.communitydragon.org/latest/game/assets/characters/tft16_malzahar/hud/tft16_malzahar_square.tft_set16.png
- Rek'Sai:    https://raw.communitydragon.org/latest/game/assets/characters/tft16_reksai/hud/tft16_reksai_square.tft_set16.png
- Cho'Gath:   https://raw.communitydragon.org/latest/game/assets/characters/tft16_chogath/hud/tft16_chogath_square.tft_set16.png
- Kai'Sa:     https://raw.communitydragon.org/latest/game/assets/characters/tft16_kaisa/hud/tft16_kaisa_square.tft_set16.png
- Bel'Veth:   https://raw.communitydragon.org/latest/game/assets/characters/tft16_belveth/hud/tft16_belveth_square.tft_set16.png
- Volibear:   https://raw.communitydragon.org/latest/game/assets/characters/tft16_volibear/hud/tft16_volibear_square.tft_set16.png
- Swain:      https://raw.communitydragon.org/latest/game/assets/characters/tft16_swain/hud/tft16_swain_square.tft_set16.png
- Shyvana:    https://raw.communitydragon.org/latest/game/assets/characters/tft16_shyvana/hud/tft16_shyvana_square.tft_set16.png
- Rift Herald: https://raw.communitydragon.org/latest/game/assets/characters/tft16_riftherald/hud/tft16_riftherald_square.tft_set16.png
- Baron Nashor: https://raw.communitydragon.org/latest/game/assets/characters/tft16_baronnashor/hud/tft16_baronnashor_square.tft_set16.png

## ITEM IMAGES — Replace all item img src attributes

Base URL: https://raw.communitydragon.org/latest/plugins/rcp-be-lol-game-data/global/default/assets/maps/tft/icons/items/hexcore/

Exact filenames (append to base URL):
- Rabadon's Deathcap:  tft_item_rabadonsdeathcap.tft_set13.png
- Jeweled Gauntlet:    tft_item_jeweledgauntlet.tft_set13.png
- Spear of Shojin:     tft_item_spearofshojin.tft_set13.png
- Blue Buff:           tft_item_bluebuff.tft_set13.png
- Archangel's Staff:   tft_item_archangelsstaff.tft_set13.png
- Morellonomicon:      tft_item_morellonomicon.tft_set13.png

The Kai'Sa item section should show: Rabadon's Deathcap, Jeweled Gauntlet, Spear of Shojin as the top 3 recommended items (with Blue Buff or Morellonomicon as alt).

## Instructions
1. Open index.html
2. Find every <img> tag that belongs to a champion card or item display
3. Replace their src attributes with the exact URLs above
4. Remove any old ddragon.leagueoflegends.com URLs for champions — replace them all with the communitydragon.org URLs above
5. Keep all onerror="this.style.display='none'" attributes
6. Keep all styles and class names intact — only change src values

Then:
1. git add index.html
2. git commit -m "fix: use correct TFT CDN URLs for all champion and item images"
3. git push origin master

When done, run:
openclaw system event --text "Done: Image URLs fixed and pushed" --mode now
