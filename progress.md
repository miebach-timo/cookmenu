# Kuchisabishii — Projektfortschritt

Animierter GSAP-One-Pager für ein japanisch inspiriertes 8-Gänge-Dinner (8 Personen),
gehostet über GitHub Pages.

**Live:** https://miebach-timo.github.io/cookmenu/  (von Branch `main`)

## Branches
- **`main`** — einziger Branch, Default + Live-Stand (GitHub Pages).
  Der frühere Arbeits-Branch `claude/gsap-menu-onepager-9c8v2p` ist gemergt und gelöscht.

## Fertig ✅
- Cover/Hero mit Ensō-Draw-Animation und Kanji 口寂しい
- Loopende Blur-Transition: Titel „Kuchisabishii" ↔ deutsche Definition
- 9 Gänge mit Rezepten (Zutaten + Zubereitung)
- Scroll-Reveals (GSAP ScrollTrigger), Parallax-Wasserzeichen, Fortschritts-Ensō oben rechts
- Mobile First inkl. mobiler Bottom-Bar mit Sprungmenü
- Dark Mode mit Toggle (folgt System-Default, merkt sich Wahl in localStorage, kein Flackern)
  - **Dark Mode nur Blau + Weiß** — Gold (`--yuzu`) und Grün (`--shiso`) sind dort auf
    Weiß bzw. tieferes Blau umgebogen; Makro-Chart bleibt über drei Blau/Weiß-Töne unterscheidbar.
- Favicon + App-Icons aus dem Kanji 口 (als Vektorpfad, schriftunabhängig)
- Pro Gericht Tabs: **Rezept · Makros · Vitamine** (Nährwerte je Portion — Näherungswerte)
- **Gang 01 (Amuse): Gericht-Foto** (`assets/amuse.png`) neben dem Kopf — zweispaltig ab 901px,
  mobil gestapelt. GSAP-Reveal: wischt beim Reinscrollen von unten hoch (`clip-path` + Zoom).

## Verworfen ✗
- Frame-Scrub-Anrichte-Animation (9 Frames, Pin/Crossfade) für Gang 01 — wieder entfernt.
- 3D-Modell (`ramen_assets_v2.glb`) als Hero/Preloader — experimentiert, dann komplett verworfen
  (Modell war ein einziger fusionierter Mesh ohne Rig/Animation → keine bewegten Tücher möglich).

## Nächste Schritte
1. `assets/amuse.png` (~2,3 MB) → WebP verkleinern (~200–400 KB), `<img>`-Quelle umstellen.
2. Optional: Foto freistellen (der graue Verlaufs-Hintergrund ist ins PNG eingebacken).
3. Optional: Fotos für die übrigen Gänge nach gleichem Muster ergänzen.

## Lokale Entwicklung
```bash
git clone https://github.com/miebach-timo/cookmenu.git
cd cookmenu
python3 -m http.server 8000   # danach http://localhost:8000
```

## Struktur
```
index.html            komplette Seite (Markup, CSS, JS/GSAP inline)
assets/js/            GSAP 3.13 lokal (core, ScrollTrigger, ScrollToPlugin)
assets/icons/         Favicon-/App-Icon-PNGs (aus Kanji 口)
assets/amuse.png      Gericht-Foto Gang 01 (noch als PNG, WebP steht aus)
favicon.svg           Kanji 口 als Vektorpfad
site.webmanifest      PWA-Manifest (Home-Bildschirm)
.nojekyll             deaktiviert Jekyll auf GitHub Pages
```

## Technische Notizen
- GSAP liegt **lokal** (kein CDN) — Seite ist self-contained; ohne JavaScript voll lesbar.
- Alle Animationen respektieren `prefers-reduced-motion`.
- WebP-Konvertierung via Python **Pillow**; Icons via **fonttools** (Glyph 口 → SVG-Pfad).
- Nährwerte sind **geschätzte** Näherungswerte je Portion (1/8 des Rezepts),
  keine laborgenauen Angaben.
