# blech'n'takt Landing Page

## Projektbeschreibung

Landing Page für **blech'n'takt**, eine Blech- und Blasmusik-Combo mit Schlagzeug aus dem Breisgau (3 Trompeten, Posaune, Euphonium, Tuba, Drums). Buchbares Live-Format für Vereinsfeste, Stadtfeste, Hallenabende, Hochzeiten und Open-Air-Sets — "Tradition trifft Moderne: Rock, Pop & Blasmusik".

**Conversion-Ziel:** Anrufen unter **0171/9900177** für Booking-Anfragen. Mobile = tap-to-call. Sekundäre Aktionen: Instagram folgen (@blech_n_takt), Termine entdecken, Live-Videos ansehen.

## Zielgruppe

Drei gleichberechtigte Gruppen:

1. **Eventveranstalter (Booker)** — Vereinsvorstände, Festwirte, Stadtfest-Organisatoren, Hochzeitspaare. Wollen wissen: Wie klingen die? Wie sehen die aus? Spielen die regelmäßig? Wie buche ich?
2. **Fans & Publikum** — Leute, die euch live gesehen haben oder über Insta gefunden haben. Wollen: Termine, neue Videos, Repertoire, Insta-Follow.
3. **Presse & Medien** — Lokalzeitungen, Radio, Blogs. Brauchen: Pressefotos, Kurz-Bandinfo, Booking-Kontakt.

Tech-Affinität gemischt — Page muss auf Boomer-Smartphone genauso funktionieren wie auf MacBook.

## Tonalität & Sprache

- **Du-Form** durchgängig, locker, mit Augenzwinkern, nahbar
- **Kein Marketing-Sprech**, keine Buzzwords ("revolutionär", "einzigartig", "Nr. 1")
- Sprache wie aus dem Info-Doc (07_Marketing/Info_Material): "Tradition trifft Moderne", "Blasmusik mit Herz 'n Beat", "Show mit Zug"
- Direkt, bodenständig, regional verwurzelt
- Kein Schwäbisch / Dialekt im Text — verständlich für alle DACH-Besucher

## Tech Stack

- **Frontend:** Vanilla HTML5 + CSS3 (kein Build-Step)
- **Keine Frameworks:** kein Tailwind, kein Bootstrap, kein React/Vue
- **JavaScript:** nur wenn strikt nötig (z. B. Mobile-Menü, Video-Lazy-Load), Vanilla JS
- **Fonts:** Inter via Google Fonts (Brand-Standard, weights 400/600/700/800/900)
- **Assets:** SVG für Icons; JPG/WebP für Fotos (komprimiert); Videos extern eingebettet (Insta/YouTube), nicht selbst gehostet

## Design-Prinzipien

**Quelle:** Brand-System aus `~/.claude/skills/blechntakt-instagram/skill.md`, ergänzt um Landing-Page-spezifische Tokens.

**Stil-Charakter:** Dunkel-dominiert, kontraststark, kompromisslos einfarbig (Schwarz + Rot + Weiß). Keine Pastelle, keine Verläufe außer dunklen Overlays über Fotos. Ein Akzent (Rot) — der wird sparsam, aber gezielt gesetzt: Buttons, das **N**, Section-Titel-Akzent.

**Drei Leitsätze:**

1. **Schwarz ist die Bühne** — der Hintergrund leuchtet nicht, er rahmt. Fotos und Content stehen darauf wie auf einer Bühne unter Scheinwerfern.
2. **Rot ist der Schlag** — wird nur eingesetzt, wo Wirkung hin soll: CTA, das N, Akzent-Linien. Niemals Block-Flächen aus Rot über mehrere Sections (Ausnahme: Booking-Block).
3. **Inter ist die Stimme** — eine Schriftart, viele Gewichte. 900 für Headlines, 700 für Buttons/Karten-Titel, 400/600 für Body. Keine zweite Schrift.

**Layout-Prinzipien:**

- **Mobile-first:** Base = 1fr-Stack, dann Breakpoints `720px` (Tablet) und `960px` (Desktop)
- **Großzügige vertikale Pads:** `--space-2xl` (96px) Desktop / `--space-xl` (64px) Mobile zwischen Sections
- **max-width 1200px** für Content-Container, mittig
- **Asymmetrie erlaubt:** z. B. Hero-Foto rechts mit Text-Spalte links — Mittigkeit ist nicht heilig

## Farbpalette

```css
:root {
  /* Brand colors */
  --color-bg: #161618;             /* Body background — fast schwarz, nahtlos zum Logo */
  --color-bg-deep: #0c0c0e;        /* Sections mit Tiefen-Wirkung (Videos, Termine) */
  --color-bg-card: #1c1c1f;        /* Karten-Hintergrund (gig-card, rep-cat) */
  --color-bg-darkest: #0a0a0c;     /* Footer */

  --color-accent: #B22325;         /* Brand-Rot (Akzent, CTA, das N) */
  --color-accent-hover: #9a1d1f;   /* CTA-Hover (10% dunkler) */
  --color-accent-on-light: #B22325;

  --color-text: #FFFFFF;
  --color-text-muted: rgba(255, 255, 255, 0.85);
  --color-text-soft: rgba(255, 255, 255, 0.6);
  --color-text-faint: rgba(255, 255, 255, 0.4);  /* Footer-Stil */

  --color-success: #22C55E;        /* Bestätigt-Badge, Häkchen */
  --color-warn: #FFC107;           /* Unbestätigt-Badge */

  --color-border: rgba(255, 255, 255, 0.08);
  --color-border-subtle: rgba(255, 255, 255, 0.06);

  /* Type scale */
  --font-family-base: 'Inter', system-ui, -apple-system, sans-serif;
  --font-size-h1: clamp(40px, 6vw, 80px);
  --font-size-h2: clamp(32px, 4.5vw, 56px);
  --font-size-h3: 24px;
  --font-size-lead: 18px;
  --font-size-body: 16px;
  --font-size-small: 14px;
  --font-size-micro: 12px;

  --line-height-tight: 1.05;
  --line-height-normal: 1.5;
  --line-height-relaxed: 1.6;

  /* Spacing */
  --space-xs: 8px;
  --space-sm: 16px;
  --space-md: 24px;
  --space-lg: 32px;
  --space-xl: 64px;
  --space-2xl: 96px;
  --space-3xl: 120px;

  /* Border radius */
  --radius-sm: 4px;
  --radius-md: 8px;
  --radius-lg: 12px;

  /* Motion */
  --transition-fast: 0.15s ease;
  --transition-base: 0.2s ease;
  --transition-slow: 0.3s ease;

  /* Layout */
  --container-max: 1200px;
  --content-max: 800px;

  /* Z-index */
  --z-sticky: 100;
}

/* Reduced-Motion-Override */
@media (prefers-reduced-motion: reduce) {
  :root {
    --transition-fast: 0.001ms;
    --transition-base: 0.001ms;
    --transition-slow: 0.001ms;
  }
}
```

## Projektstruktur

```
blechNtakt_Landingpage/
├── CLAUDE.md              ← Diese Datei
├── index.html             ← Single-Page
├── styles.css             ← Alle Styles
├── impressum.html         ← Pflicht-Seite
├── datenschutz.html       ← Pflicht-Seite
├── assets/
│   ├── logo.svg
│   ├── photos/            ← Auftrittsfotos (komprimiert)
│   └── icons/             ← SVG-Icons
└── specs/
    └── features/          ← Feature-Specs pro Section
```

## Code-Regeln

- Alle **sichtbaren Texte** auf Deutsch
- **Variablen, Klassen, Kommentare**: Englisch
- **Semantisches HTML:** `<header>`, `<section>`, `<nav>`, `<footer>` — kein Div-Soup
- `<html lang="de">` setzen
- **CSS-Klassen:** Komponenten-orientiert (`.hero`, `.gigs__item`), keine Utility-Klassen
- **Keine** Drittanbieter-Tracker, keine Cookie-Banner
- **JSON/Code:** Nur gerade Anführungszeichen `"` `'`, niemals typografische
- **Das N in "BLECH'N'TAKT" ist IMMER rot** — als Klasse `.red-n` (Brand-Konstante)

## Komponenten & Patterns

### Globale Patterns

**`.red-n`** — Das **N** in "BLECH'N'TAKT" und in Headlines/Footer-Text:
```css
.red-n { color: var(--color-accent); }
.red-n-on-red { color: var(--color-bg); }   /* wenn auf rotem BG (Booking) */
```

**`.section-title`** (H2 für jede Section):
```css
.section-title {
  font-weight: 800;
  font-size: var(--font-size-h2);
  line-height: var(--line-height-tight);
  color: var(--color-text);
  margin-bottom: var(--space-md);
}
.section-title .accent { color: var(--color-accent); }
```

**`.section-padding`** (Wrapper-Klasse für Section-Pads):
- Desktop: `padding: var(--space-2xl) var(--space-md);`
- Mobile: `padding: var(--space-xl) var(--space-sm);`

### Buttons

**`.btn--primary`** — der CTA-Standard:
```css
.btn--primary {
  display: inline-block;
  background: var(--color-accent);
  color: var(--color-text);
  padding: 18px 32px;
  font-size: 18px;
  font-weight: 700;
  border-radius: var(--radius-md);
  text-decoration: none;
  min-height: 56px;
  transition: background var(--transition-base), transform var(--transition-base);
}
.btn--primary:hover { background: var(--color-accent-hover); transform: translateY(-1px); }
.btn--primary:focus-visible { outline: 2px solid var(--color-text); outline-offset: 2px; }
```

**`.btn--ghost`** — sekundäre CTAs:
```css
.btn--ghost {
  border: 1px solid var(--color-text);
  color: var(--color-text);
  background: transparent;
  /* sonst gleiche Properties wie --primary */
}
```

### Cards

**`.card`** — Basis für `gig-card`, `rep-cat`, `reel-card`:
```css
.card {
  background: var(--color-bg-card);
  border: 1px solid var(--color-border);
  border-radius: var(--radius-lg);
  padding: var(--space-md);
}
```

**`.badge`** — Status-Indikatoren (bestätigt / unbestätigt):
```css
.badge { padding: 4px 10px; border-radius: var(--radius-sm); font-size: var(--font-size-micro); display: inline-block; }
.badge--confirmed { background: rgba(34,197,94,.15); color: var(--color-success); }
.badge--tentative { background: rgba(255,193,7,.15); color: var(--color-warn); }
```

### Mobile-Sticky-Call-Bar

**`.sticky-call`** — fixierter Tel-Button auf Mobile:
```css
.sticky-call {
  position: fixed;
  bottom: 0; left: 0; right: 0;
  background: var(--color-accent);
  color: var(--color-text);
  padding: 16px;
  text-align: center;
  font-weight: 700;
  text-decoration: none;
  z-index: var(--z-sticky);
  display: none;
}
@media (max-width: 719px) { .sticky-call { display: block; } }
```

### Sections im Überblick (Background-Wechsel)

| Section | Background | Begründung |
|---|---|---|
| Hero | `--color-bg` mit Foto-Overlay | Atmosphäre |
| Über uns | `--color-bg` | Standard |
| Videos | `--color-bg-deep` | Tiefe-Effekt, "ins Video tauchen" |
| Galerie | `--color-bg` | Bilder atmen lassen |
| Termine | `--color-bg-deep` | abwechselnde Tiefen-Wirkung |
| Repertoire | `--color-bg` | Standard |
| Booking | `--color-accent` (Rot!) | **DER** visuelle Höhepunkt |
| Footer | `--color-bg-darkest` | dezenter Abschluss |

### Globale Reset & Base

```css
*, *::before, *::after { box-sizing: border-box; }
body {
  margin: 0;
  font-family: var(--font-family-base);
  background: var(--color-bg);
  color: var(--color-text);
  font-size: var(--font-size-body);
  line-height: var(--line-height-normal);
  -webkit-font-smoothing: antialiased;
}
img { max-width: 100%; height: auto; display: block; }
html { scroll-behavior: smooth; }
@media (prefers-reduced-motion: reduce) {
  html { scroll-behavior: auto; }
}
:focus-visible { outline: 2px solid var(--color-accent); outline-offset: 2px; }
```

## Accessibility

- WCAG AA: Kontrast 4.5:1 für Body-Text auf schwarzem Hintergrund
- Tastatur-Navigation: alle CTAs, Links, Akkordeons fokussierbar
- `:focus-visible`-Outline sichtbar (Brand-Rot oder Weiß)
- `prefers-reduced-motion` respektieren — Übergänge auf 0.001ms
- Alt-Texte: alle Bandfotos, leere Alt-Texte nur für rein dekorative Bilder
- Tel-Link mit `aria-label="Jetzt anrufen für Booking-Anfrage"`
- Mobile Touch-Targets: min 44×44px

## Performance

- Ziel: erstes Render < 250 KB (HTML + CSS + Inter-Font + Hero-Foto)
- Hero-Foto: WebP mit JPG-Fallback, max ~80 KB
- Weitere Fotos: lazy-loaded (`loading="lazy"`), max ~60 KB pro Bild
- Videos: extern eingebettet (Insta/YouTube), nicht autoplay, lazy
- Inter-Font: nur die wirklich genutzten Weights (z. B. 400, 700, 900)
- Progressive Enhancement: Page funktioniert ohne JavaScript
- Mobile-First: Base-CSS = 1fr-Stack, dann `min-width`-Queries

## Deployment

- **GitHub Pages** (öffentliches Repo, Markdown-Cleanup vor Push)
- Vor Live-Schaltung: iPad/iOS-Safari getestet
- Eigene Domain (`blechntakt.de` o. ä.) optional später dranhängen

## Wichtig

**Pflicht-Elemente:**

- Logo (aus `~/Desktop/Blech\`N\`Takt /05_Bilder/Logo/`)
- Tel-Nummer **0171/9900177** mehrfach (Hero-CTA + Footer + sticky Mobile-CTA)
- Impressum mit ladungsfähiger Adresse (User liefert in Phase 5)
- Datenschutz-Seite (Standard-Text für statische Page ohne Tracker)
- Instagram-Link **@blech_n_takt** sichtbar
- Facebook-Link **bit.ly/FB_blechtakt** sichtbar
- Live-Videos / Reels (eingebettet von Insta oder YouTube)
- Bandfotos / Auftrittsfotos (aus `05_Bilder/2024`)
- Aktuelle Termine 2026 (aus `06_Verwaltung/Termine/Termine 2026.xlsx`)
- Repertoire-Auszug (aus `02_Repertoire/Aktuell/Repertoire 2026 B´n´T.pdf`)

**No-Gos:**

- Kein Auto-Play von Videos oder Audio
- Keine Stockfotos / generische Brass-Band-Bilder — nur eigene Fotos
- Keine Marketing-Buzzwords ("revolutionär", "Game-Changer", "Nr. 1 in der Region")
- Keine Tracker / Analytics-Skripte (Default — kann später bewusst ergänzt werden)
- Kein Cookie-Banner
- Kein Dialekt im Text

**Brand-Konstanten (aus Insta-Skill):**

- Hintergrund: `#161618` (fast schwarz, nahtlos zum Logo)
- Akzent-Rot: `#B22325` (für Flächen, Text, Rahmen, das N)
- Weiß: `#FFFFFF`, gedämpft: `rgba(255,255,255,0.85)`, Footer: `rgba(255,255,255,0.4)`
- Grün-Check: `#22C55E` (für ✓-Listen)
- Font: Inter (Google Fonts)
- Tagline: "Follow the Takt!" / "Blasmusik mit Herz 'n Beat"
- Visuelle Signature: schwarzer Look, Hosenträger, **rote Schuhe**

**Sonstiges:**

- Wenn etwas nicht klappt: Fehler benennen, Fix vorschlagen — nicht entschuldigen
- Keine unnötigen Sicherheitshinweise bei harmlosen Anfragen
