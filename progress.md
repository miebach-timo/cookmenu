# Kuchisabishii — Projektfortschritt

Animierter GSAP-One-Pager für ein japanisch inspiriertes 9-Gänge-Dinner (10 Personen),
gehostet über GitHub Pages.

**Live:** https://miebach-timo.github.io/cookmenu/  (von Branch `main`)

## Branches
- **`main`** — Live-Stand (GitHub Pages). Stabil, ohne die noch offene Amuse-Animation.
- **`claude/gsap-menu-onepager-9c8v2p`** — Arbeits-Branch mit der fertig gebauten,
  aber noch nicht freigegebenen Scroll-Animation.

## Fertig ✅
- Cover/Hero mit Ensō-Draw-Animation und Kanji 口寂しい
- Loopende Blur-Transition: Titel „Kuchisabishii" ↔ deutsche Definition
- 9 Gänge mit Rezepten (Zutaten + Zubereitung)
- Scroll-Reveals (GSAP ScrollTrigger), Parallax-Wasserzeichen, Fortschritts-Ensō oben rechts
- Mobile First inkl. mobiler Bottom-Bar mit Sprungmenü
- Dark Mode mit Toggle (folgt System-Default, merkt sich Wahl in localStorage, kein Flackern)
- Favicon + App-Icons aus dem Kanji 口 (als Vektorpfad, schriftunabhängig)
- Pro Gericht Tabs: **Rezept · Makros · Vitamine** (Nährwerte je Portion — Näherungswerte)

## In Arbeit 🚧 — Anrichte-Animation Gang 01 (Amuse)
- Scroll-Scrub-Animation (Pin + Crossfade über 9 Frames) ist **gebaut und getestet** —
  liegt nur auf `claude/gsap-menu-onepager-9c8v2p`, noch **nicht** auf `main`.
- **Offen:** Die zuerst gelieferten Frames waren nicht wirklich transparent
  (Schachbrett-Muster als Pixel eingebrannt, `mode RGB` ohne Alphakanal).
  → Benötigt werden **9 echt transparente PNGs**:
  - gleiche Leinwand/Position für alle Frames (Teller darf nicht „springen"),
  - Reihenfolge `amuse-1` = Zutaten schweben … `amuse-9` = fertig angerichtet,
  - Ablage in `assets/anim/amuse/`.
- Die nicht-transparenten Quell-PNGs wurden wieder entfernt. Die aktuellen `.webp`
  sind Platzhalter und werden ersetzt, sobald saubere Frames vorliegen.

## Nächste Schritte
1. 9 transparente PNGs nach `assets/anim/amuse/` liefern.
2. Zu WebP konvertieren (Python Pillow, quality ~84) und einen Frame gegen Hell/Dunkel prüfen.
3. Feature-Branch → `main` mergen → Animation geht live.

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
assets/anim/amuse/    Frames der Amuse-Animation (WebP; Quell-PNGs entfernt)
favicon.svg           Kanji 口 als Vektorpfad
site.webmanifest      PWA-Manifest (Home-Bildschirm)
.nojekyll             deaktiviert Jekyll auf GitHub Pages
```

## Technische Notizen
- GSAP liegt **lokal** (kein CDN) — Seite ist self-contained; ohne JavaScript voll lesbar.
- Alle Animationen respektieren `prefers-reduced-motion`.
- WebP-Konvertierung via Python **Pillow**; Icons via **fonttools** (Glyph 口 → SVG-Pfad).
- Nährwerte sind **geschätzte** Näherungswerte je Portion (1/10 des Rezepts),
  keine laborgenauen Angaben.
