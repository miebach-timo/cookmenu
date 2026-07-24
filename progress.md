# Kuchisabishii — Projektfortschritt

Animierter GSAP-One-Pager für ein japanisch inspiriertes 7-Gänge-Dinner (8 Personen),
gehostet über GitHub Pages.

**Live:** https://miebach-timo.github.io/cookmenu/  (von Branch `main`)
**QR-Code zur Live-URL:** `assets/qr-cookmenu.png` / `assets/qr-cookmenu.svg`

## Branches
- **`main`** — einziger Branch, Default + Live-Stand (GitHub Pages).

## Menü-Reihenfolge (7 Gänge)
1. **Amuse** — Marinierte Nashi · Miso-Nashi-Creme · Yuzu-Gel *(vegan)*
2. **Nigiri — Dreierlei** — Aburi-Tomate · Zucchini-„Unagi" · Kräuterseitling-„Hotate" *(vegetarisch – Butter im Reis)*
3. **Yakitori-Spieße** — Hähnchen & Wonderchunks · Citrus Tare *(vegan/Fleisch)*
4. **Mariniertes Grillgemüse** — Kräuterseitling · Paprika · Zucchini *(vegan)*
5. **Avocado Salat** — Avocado · Sesam-Dressing *(vegan)*
6. **Yuzu Ponzu** — Dip zu Yakitori & Grillgemüse *(vegan)*
7. **Dessert** — Kokos-Yuzu-Eis · Zitrone · schwarzer Sesam *(vegan)*

Rezepte auf **8 Personen** skaliert; Nährwerte je Portion = 1/8 des Rezepts (Näherungswerte).

**Änderung (2026-07-24):** Nasu Dengaku (Aubergine) entfernt; Nigiri von Gang 05 auf Gang 02
(nach dem Amuse) vorgezogen und zum Dreierlei erweitert — Aburi-Tomate plus neue Zucchini-„Unagi"
und Kräuterseitling-„Hotate" mit gemeinsamer Kabayaki-Glasur. Interne Section-ID bleibt `c6`
(Anchor/JS filtern über fehlende IDs), `assets/nasu.png` bleibt ungenutzt im Repo.

## Fertig ✅
- **Hero mit Video-Hintergrund** (`assets/hero.mp4`): nahtloser Loop (End-zu-Anfang-Crossfade
  in ffmpeg, 1080p, tonlos, ~4 MB) im `.hero-bg`-Container; **Aurora-Overlay**
  (CSS-Port des Aceternity-Effekts) darüber. Beim Runterscrollen fadet der Hintergrund nach oben
  aus und beim Hochscrollen wieder ein (GSAP ScrollTrigger, scrub).
  `assets/hero-bg.png` bleibt als Fallback (CSS-`background` + `poster`) für No-JS und
  `prefers-reduced-motion` (da wird das `<video>` ausgeblendet).
- **Hero-Titel**: großes Kanji 口寂しい (Ensō-Ring entfernt). Intro-Reihenfolge
  **Kanji (Fade) → „KUCHISABISHII" (Zeichen-Stagger) → „JAPANESE DINNER" (Fade)**,
  danach Loop Wort ↔ englische Definition („Lonely mouth — for the sake of eating.").
- Hero-Farbe **fix in beiden Modi** (`--hero-ink`, dunkel) — Kanji + Text immer lesbar aufm Bild.
- Scroll-Cue am Grün-Anfang, schwarz; Linien-Puls dezent.
- Alle **7 Gänge mit Gericht-Foto** (Foto-neben-Titel-Layout, ab 641px zweispaltig, mobil gestapelt;
  GSAP-Reveal wischt von unten hoch).
- Pro Gericht Tabs **Rezept · Makros · Vitamine** + **Diät-Badge** (vegan/vegetarisch/Fleisch).
- Info-Hinweise ohne Kasten, als „Info: …"-Präfix.
- Scroll-Reveals, Parallax-Wasserzeichen (壱–七), Fortschritts-Ensō oben rechts
  (gleich groß wie Theme-Toggle).
- Seitliche Navigation (Rail links, Side-Kanji rechts) blendet erst **nach** dem Hero ein;
  mobil Bottom-Bar mit Sprungmenü.
- Dark Mode mit Toggle (folgt System, merkt Wahl in localStorage, kein Flackern).
- **Farbschema nur Schwarz/Weiß (+ Gold-Akzent).** Blau (`--indigo`) komplett entfernt/neutralisiert;
  Aurora in Graustufen.
- **Aurora-Overlay modus-unabhängig**: in Light *und* Dark identisch (heller Look als Default),
  neutrale Graustufen (`--ar1`–`--ar4`), Opacity `.35`, `multiply`-Blend. Streifen nutzt festes
  Washi (`--ar-paper`), damit im Dark Mode nichts umschlägt. (Warme Farben getestet, wieder verworfen.)
- Favicon + App-Icons aus dem Kanji 口 (Vektorpfad, schriftunabhängig).

## Verworfen ✗
- Ensō-Ring im Hero (Draw-Animation, dann glassy/RGB-Split/Liquid-Glass-Varianten) — komplett entfernt.
- Frame-Scrub-Anrichte-Animation & 3D-Modell (`.glb`) — früher verworfen.

## Nächste Schritte
1. **Bilder komprimieren**: `hero-bg.png` (~8,5 MB) und die Gericht-Fotos (~0,8–1 MB je)
   → WebP/JPEG, `<img>`/`background`-Quellen umstellen.
2. Optional: Foto-Hintergründe freistellen (grauer Verlauf ist teils ins PNG eingebacken).

## Struktur
```
index.html            komplette Seite (Markup, CSS, JS/GSAP inline)
assets/js/            GSAP 3.13 lokal (core, ScrollTrigger, ScrollToPlugin)
assets/icons/         Favicon-/App-Icon-PNGs (aus Kanji 口)
assets/hero.mp4       Hero-Video (nahtloser Loop, 1080p, tonlos)
assets/hero-bg.png    Hero-Standbild (Fallback + Video-Poster)
assets/*.png          Gericht-Fotos: amuse, nasu, yakitori, grillgemuese,
                      nigiri, avocado, ponzu, eis
assets/qr-cookmenu.*  QR-Code (PNG + SVG) zur Live-URL
favicon.svg           Kanji 口 als Vektorpfad
site.webmanifest      PWA-Manifest (Home-Bildschirm)
.nojekyll             deaktiviert Jekyll auf GitHub Pages
```

## Technische Notizen
- GSAP liegt **lokal** (kein CDN) — Seite ist self-contained; ohne JavaScript voll lesbar.
- Alle Animationen respektieren `prefers-reduced-motion`.
- Interne Section-IDs (`c1`, `c2`, `c4`–`c9`) sind **nicht** sequenziell (Gang 02+03 wurden
  einst gemergt); nur die angezeigten Nummern/Wasserzeichen und Listen werden neu vergeben.
  Anchor-Links und das JS-Label-Array filtern fehlende IDs.
- Nährwerte sind **geschätzte** Näherungswerte je Portion (1/8 des Rezepts).

## Lokale Entwicklung
```bash
git clone https://github.com/miebach-timo/cookmenu.git
cd cookmenu
# beliebiger statischer Server, z. B.:
npx serve .          # oder: python3 -m http.server 8000
```
