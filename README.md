# 口寂しい — Kuchisabishii

Ein japanisch inspiriertes Dinner in neun Gängen für zehn Personen — als animierter GSAP-One-Pager.

## Features

- **Ensō-Intro**: Der Ensō-Kreis zeichnet sich beim Laden selbst, die Kanji 口寂しい blenden gestaffelt ein
- **Scroll-Reveals**: Überschriften, Zutatenlisten und Zubereitungsschritte erscheinen kaskadierend beim Scrollen (GSAP ScrollTrigger)
- **Parallax-Wasserzeichen**: Japanische Zahlzeichen (壱・弐・参 …) wandern hinter jedem Gang
- **Fortschritts-Ensō**: Kreis oben rechts zeigt den Lesefortschritt in Prozent, Klick scrollt sanft nach oben
- **Nährwert-Tabs**: Pro Gang ein Tab-Menü („Makros" / „Vitamine") mit den Näherungswerten je Portion (1/10 des Rezepts) — kcal, Protein/Fett/Kohlenhydrate, Energieverteilungs-Balken, Detailwerte und Mikronährstoffe; per Tastatur bedienbar (Pfeiltasten) und ohne JavaScript vollständig lesbar
- **Mobile First**: Basis-Layout für kleine Screens, Desktop-Erweiterungen per `min-width`-Queries
- **Mobile Navigation**: Bottom-Bar mit aktuellem Gang und Vollbild-Sprungmenü (献立); auf Desktop stattdessen seitliche Punkte-Rail mit aktiven Zuständen und Smooth Scroll
- **Barrierefrei**: Respektiert `prefers-reduced-motion`; ohne JavaScript bleibt die Seite vollständig lesbar
- **Dark Mode**: Toggle oben rechts; folgt standardmäßig dem System (`prefers-color-scheme`), merkt sich die manuelle Wahl in `localStorage` und setzt das Theme vor dem ersten Paint (kein Flackern)
- **Icons**: Favicon mit dem Kanji 口 (aus dem Titel 口寂しい) als schriftunabhängiger Vektorpfad im SVG, plus PNG-Fallbacks, Apple-Touch-Icon und `site.webmanifest` für „Zum Home-Bildschirm" auf iOS/Android
- **Selbstständig**: GSAP liegt lokal unter `assets/js/` — keine externen Script-CDNs nötig

## Über GitHub Pages hosten

1. Branch in `main` mergen (oder direkt den Branch verwenden)
2. Im Repository: **Settings → Pages**
3. Unter **Build and deployment → Source**: „Deploy from a branch" wählen
4. Branch (`main`) und Ordner (`/ (root)`) auswählen, **Save**
5. Nach ca. einer Minute ist die Seite unter `https://<username>.github.io/cookmenu/` erreichbar

## Struktur

```
index.html              — komplette Seite (Markup, Styles, Animationen)
assets/js/              — GSAP 3.13 (Core, ScrollTrigger, ScrollToPlugin)
.nojekyll               — deaktiviert Jekyll-Verarbeitung auf GitHub Pages
```
