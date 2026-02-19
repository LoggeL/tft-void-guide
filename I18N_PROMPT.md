Add a German/English language toggle to index.html.

## APPROACH
1. Add `data-i18n="key"` attributes to all translatable text elements
2. Create a `translations` JS object with `en` and `de` keys for every string
3. Add `applyLang(lang)` function that swaps all text
4. Add a sticky language toggle button in the top-right corner (or in the hero area)
5. Store preference in localStorage

## TOGGLE BUTTON DESIGN
Add a fixed button in the top-right corner:
```html
<button id="lang-toggle" onclick="toggleLang()" 
  style="position:fixed;top:1rem;right:1rem;z-index:9999;
  background:rgba(139,92,246,0.15);border:1px solid rgba(139,92,246,0.4);
  color:#a78bfa;font-family:var(--font-display);font-size:0.8rem;
  padding:0.5rem 1rem;border-radius:4px;cursor:pointer;
  backdrop-filter:blur(8px);letter-spacing:0.1em;transition:all 0.2s;">
  🇩🇪 DE
</button>
```

When in DE mode, show "🇬🇧 EN" to switch back.

## JS LOGIC
```js
let currentLang = localStorage.getItem('lang') || 'en';

function applyLang(lang) {
  currentLang = lang;
  localStorage.setItem('lang', lang);
  document.querySelectorAll('[data-i18n]').forEach(el => {
    const key = el.getAttribute('data-i18n');
    if (translations[lang] && translations[lang][key]) {
      el.innerHTML = translations[lang][key];
    }
  });
  document.getElementById('lang-toggle').innerHTML = lang === 'en' ? '🇩🇪 DE' : '🇬🇧 EN';
}

function toggleLang() {
  applyLang(currentLang === 'en' ? 'de' : 'en');
}

// Apply on load
document.addEventListener('DOMContentLoaded', () => applyLang(currentLang));
```

## TRANSLATIONS OBJECT
```js
const translations = {
  en: {
    // Nav/Hero
    "hero.subtitle": "SET 16 | PATCH 16.4",
    "hero.tagline": "Classified Intel — Void Comp Breakdown",
    "hero.scroll": "SCROLL TO ACCESS",
    // Section titles
    "section.champions": "CHAMPIONS",
    "section.leveling": "LEVELING GUIDE",
    "section.positioning": "POSITIONING",
    "section.stages": "STAGE BREAKDOWN",
    "section.items": "ITEMS & MUTATIONS",
    // Trait pills / stats
    "trait.void": "9x Void",
    "trait.bruiser": "2x Bruiser",
    "trait.longshot": "Longshot",
    // Stage labels
    "stage.early.badge": "STAGE 2-3",
    "stage.early.title": "Early Game",
    "stage.mid.badge": "STAGE 4",
    "stage.mid.title": "Mid Game",
    "stage.late.badge": "STAGE 5+",
    "stage.late.title": "Late Game",
    // Stage bullets (early)
    "stage.early.b1": "<strong>Slam items aggressively</strong> — don't save components",
    "stage.early.b2": "<em>Play for winstreak</em> to build gold interest buffer",
    "stage.early.b3": "Run Kog'Maw + Malzahar + Rek'Sai as core",
    "stage.early.b4": "Keep strongest available board — don't force economy at cost of HP",
    // Rift Herald unlock
    "unlock.rift.title": "🌀 RIFT HERALD UNLOCK",
    "unlock.rift.b1": "Have <strong>Void active</strong> for <strong>8 player combats</strong>",
    "unlock.rift.b2": "No level requirement — auto-unlocks after 8 Void combats",
    "unlock.rift.b3": "<strong>2 Void units</strong> already activate the trait — get them on board ASAP to start the 8-combat counter",
    // Stage mid bullets
    "stage.mid.b1": "Roll on <strong>Level 8</strong> for key 2-stars",
    "stage.mid.b2": "Priority: <em>Kai'Sa 2★</em> first, then <em>Rift Herald 2★</em>",
    "stage.mid.b3": "Push to <strong>Level 9</strong> after stabilizing",
    "stage.mid.b4": "Flex <em>Swain</em> or <em>Shyvana</em> if available",
    "stage.mid.b5": "Never roll below 10g — interest matters",
    // Kai'Sa unlock
    "unlock.kaisa.title": "🔓 KAI'SA UNLOCK",
    "unlock.kaisa.b1": "Reach <strong>Level 7</strong>",
    "unlock.kaisa.b2": "Have a <strong>Longshot</strong> unit on board with <em>3 items equipped</em>",
    "unlock.kaisa.b3": "Both conditions met → Kai'Sa unlocks automatically",
    // Volibear unlock
    "unlock.voli.title": "⚡ VOLIBEAR UNLOCK",
    "unlock.voli.b1": "Reach <strong>Level 8</strong>",
    "unlock.voli.b2": "Have a unit that starts combat with at least <strong>3800 HP</strong>",
    "unlock.voli.b3": "Tip: Rift Herald or Cho'Gath with tank items easily hit this threshold",
    // Stage late bullets
    "stage.late.b1": "Full <strong>9 Void + Bruiser</strong> board active",
    "stage.late.b2": "Wukong → <em>Volibear</em> slot for Bruiser trait",
    "stage.late.b3": "Push <strong>Level 10</strong> when carry is itemized",
    "stage.late.b4": "Slot in <em>Baron Nashor</em> as capstone unit",
    // Baron unlock
    "unlock.baron.title": "👑 BARON NASHOR UNLOCK",
    "unlock.baron.b1": "Reach <strong>Level 10</strong>",
    "unlock.baron.b2": "Field <strong>7 unique Void units</strong> simultaneously",
    "unlock.baron.b3": "Baron counts as <strong>2 team slots</strong> — plan your roster accordingly",
    "unlock.baron.b4": "Tip: Transfer your best items to Baron immediately after unlocking",
    // Positioning tabs
    "board.lvl4.sub": "Early Opener",
    "board.lvl6.sub": "Early",
    "board.lvl8.sub": "Stable",
    "board.lvl9.sub": "Roll for Kai'Sa ⭐⭐ — Baron comes on Lvl 10",
    "board.lvl10.sub": "Full Cap",
    // Board notes
    "board.lvl4.note": "2 Void active — start the Rift Herald counter",
    "board.lvl6.note": "4 Void active — Rift Herald counter running",
    "board.lvl8.note": "6 Void active — Rift Herald unlocked",
    "board.lvl9.note": "ROLL FOR KAI'SA ⭐⭐ — BARON COMES ON LVL 10",
    "board.lvl10.note": "BARON NASHOR JOINS FRONT LINE",
    // Items section
    "items.kaisa.sub": "HYBRID CARRY BUILD",
    "items.baron.sub": "AD CARRY / BRUISER",
    "items.herald.sub": "TANK / BRUISER BUILD",
    "items.belveth.sub": "SLAYER BUILD",
    // Win condition
    "win.title": "PUSH TO LEVEL 10",
    "win.sub": "Baron Nashor — The Ultimate Carry",
    // Level timeline conditions (abbreviated for data-i18n)
    "lvl.4.cond": "Level up if you have upgrades and a good item",
    "lvl.5.cond": "Always, unless on 3× loss streak",
    "lvl.6.cond": "4+ winstreak OR stay above 40g",
    "lvl.7.cond": "If you can stay above 30g",
    "lvl.8.cond": "Roll for Kai'Sa ⭐⭐ + Rift Herald ⭐⭐",
    "lvl.9.cond": "High HP: wait until 5-5 | Low HP: go ASAP",
    "lvl.10.cond": "Carry itemized + upgraded → Baron online",
  },
  de: {
    // Nav/Hero
    "hero.subtitle": "SET 16 | PATCH 16.4",
    "hero.tagline": "Geheimakte — Void Comp Breakdown",
    "hero.scroll": "SCROLLEN UM FORTZUFAHREN",
    // Section titles
    "section.champions": "CHAMPIONS",
    "section.leveling": "LEVEL-GUIDE",
    "section.positioning": "POSITIONIERUNG",
    "section.stages": "STAGE-ÜBERSICHT",
    "section.items": "ITEMS & MUTATIONEN",
    // Trait pills
    "trait.void": "9× Void",
    "trait.bruiser": "2× Bruiser",
    "trait.longshot": "Weitschuss",
    // Stage labels
    "stage.early.badge": "STAGE 2-3",
    "stage.early.title": "Frühes Spiel",
    "stage.mid.badge": "STAGE 4",
    "stage.mid.title": "Mittelspiel",
    "stage.late.badge": "STAGE 5+",
    "stage.late.title": "Spätes Spiel",
    // Stage bullets (early)
    "stage.early.b1": "<strong>Items sofort einbauen</strong> — keine Komponenten horten",
    "stage.early.b2": "<em>Auf Winstreak spielen</em> um Goldinteresse aufzubauen",
    "stage.early.b3": "Kog'Maw + Malzahar + Rek'Sai als Kernkombo",
    "stage.early.b4": "Stärkstes Board spielen — Economy nicht auf Kosten von HP forcen",
    // Rift Herald unlock
    "unlock.rift.title": "🌀 RIFT HERALD FREISCHALTEN",
    "unlock.rift.b1": "<strong>Void aktiv</strong> für <strong>8 Spielkämpfe</strong>",
    "unlock.rift.b2": "Kein Level-Requirement — schaltet nach 8 Void-Kämpfen automatisch frei",
    "unlock.rift.b3": "<strong>2 Void-Units</strong> aktivieren den Trait bereits — so früh wie möglich auf das Board bringen",
    // Stage mid bullets
    "stage.mid.b1": "Rollen auf <strong>Level 8</strong> für wichtige 2-Sterne",
    "stage.mid.b2": "Priorität: <em>Kai'Sa 2★</em> zuerst, dann <em>Rift Herald 2★</em>",
    "stage.mid.b3": "Nach dem Stabilisieren auf <strong>Level 9</strong> pushen",
    "stage.mid.b4": "<em>Swain</em> oder <em>Shyvana</em> als Flex wenn verfügbar",
    "stage.mid.b5": "Nie unter 10g rollen — Zinsen sind wichtig",
    // Kai'Sa unlock
    "unlock.kaisa.title": "🔓 KAI'SA FREISCHALTEN",
    "unlock.kaisa.b1": "<strong>Level 7</strong> erreichen",
    "unlock.kaisa.b2": "Eine <strong>Weitschuss</strong>-Unit mit <em>3 Items ausgerüstet</em> auf dem Board haben",
    "unlock.kaisa.b3": "Beide Bedingungen erfüllt → Kai'Sa schaltet automatisch frei",
    // Volibear unlock
    "unlock.voli.title": "⚡ VOLIBEAR FREISCHALTEN",
    "unlock.voli.b1": "<strong>Level 8</strong> erreichen",
    "unlock.voli.b2": "Eine Unit haben, die mit mindestens <strong>3800 HP</strong> in den Kampf startet",
    "unlock.voli.b3": "Tipp: Rift Herald oder Cho'Gath mit Tank-Items erreichen das leicht",
    // Stage late bullets
    "stage.late.b1": "Volles <strong>9 Void + Bruiser</strong> Board aktiv",
    "stage.late.b2": "Wukong → <em>Volibear</em> Slot für Bruiser-Trait",
    "stage.late.b3">": "Auf <strong>Level 10</strong> pushen wenn Carry itemisiert ist",
    "stage.late.b4": "<em>Baron Nashor</em> als Cap-Unit einsetzen",
    // Baron unlock
    "unlock.baron.title": "👑 BARON NASHOR FREISCHALTEN",
    "unlock.baron.b1": "<strong>Level 10</strong> erreichen",
    "unlock.baron.b2": "<strong>7 einzigartige Void-Units</strong> gleichzeitig aufstellen",
    "unlock.baron.b3": "Baron zählt als <strong>2 Team-Slots</strong> — Roster entsprechend planen",
    "unlock.baron.b4": "Tipp: Beste Items sofort nach dem Freischalten auf Baron transferieren",
    // Positioning tabs
    "board.lvl4.sub": "Früher Opener",
    "board.lvl6.sub": "Früh",
    "board.lvl8.sub": "Stabilisieren",
    "board.lvl9.sub": "Für Kai'Sa 2★ rollen — Baron kommt auf Lvl 10",
    "board.lvl10.sub": "Volles Cap",
    // Board notes
    "board.lvl4.note": "2 Void aktiv — Rift Herald Zähler starten",
    "board.lvl6.note": "4 Void aktiv — Rift Herald Zähler läuft",
    "board.lvl8.note": "6 Void aktiv — Rift Herald freigeschaltet",
    "board.lvl9.note": "FÜR KAI'SA 2★ ROLLEN — BARON KOMMT AUF LVL 10",
    "board.lvl10.note": "BARON NASHOR BETRITT DIE FRONTLINIE",
    // Items section
    "items.kaisa.sub": "HYBRID-CARRY BUILD",
    "items.baron.sub": "AD CARRY / BRUISER",
    "items.herald.sub": "TANK / BRUISER BUILD",
    "items.belveth.sub": "SLAYER BUILD",
    // Win condition
    "win.title": "AUF LEVEL 10 PUSHEN",
    "win.sub": "Baron Nashor — Der ultimative Carry",
    // Level conditions
    "lvl.4.cond": "Level up wenn du Upgrades und ein gutes Item hast",
    "lvl.5.cond": "Immer, außer bei 3× Lossstreak",
    "lvl.6.cond": "4+ Winstreak ODER über 40g bleiben",
    "lvl.7.cond": "Wenn du über 30g bleiben kannst",
    "lvl.8.cond": "Für Kai'Sa 2★ + Rift Herald 2★ rollen",
    "lvl.9.cond": "Viel HP: bis 5-5 warten | Wenig HP: so früh wie möglich",
    "lvl.10.cond": "Carry itemisiert + upgraded → Baron online",
  }
};
```

## IMPLEMENTATION STEPS

1. Add the translations object in a `<script>` block near the bottom of the HTML (before closing </body>)
2. Add the lang toggle button HTML right after `<body>` opens
3. Add `data-i18n="key"` attributes to every matching text element throughout the HTML
4. Add the `applyLang` and `toggleLang` functions
5. Call `applyLang(currentLang)` on DOMContentLoaded

## KEY RULES
- Champion names (Kai'Sa, Rek'Sai, etc.) stay the same in both languages
- Item names stay English in both languages (Infinity Edge, Warmog's, etc.)  
- Item desc codes (CRIT, HP REGEN, etc.) stay English
- Rank badges (S/A/B) stay same
- Mutation names stay English
- "CLASSIFIED", "INTERNAL USE ONLY" stamps stay English (aesthetic)
- Numbers stay the same

## IMPORTANT: Fix a typo in the translations above
There is a typo on this line in the de section:
    "stage.late.b3">": "Auf...   ← remove the extra "> after the key

After implementing:
1. git add index.html
2. git commit -m "feat: EN/DE language toggle with localStorage persistence"
3. git push origin master
4. openclaw system event --text "Done: language toggle live" --mode now
