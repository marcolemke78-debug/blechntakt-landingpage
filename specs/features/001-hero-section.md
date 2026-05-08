# Feature 001 — Hero Section

**Status:** Entwurf — wartet auf User-Freigabe
**Erstellt:** 2026-05-08
**Datei(en):** `index.html`, `styles.css`

---

## Ziel

In unter 5 Sekunden zeigen: **Wer ist die Combo, wofür kann ich sie buchen, wie erreiche ich sie?** Der Besucher (Veranstalter, Fan oder Pressevertreter) muss sofort den Tel-Button sehen und ohne Nachdenken erfassen, dass es sich um eine buchbare Live-Combo handelt.

## User Story

> Als **Festwirt im Breisgau**, der einen Auftritt für sein Sommerfest sucht, lande ich auf der Hero-Section, weil mir jemand "blechntakt.de" empfohlen hat. Ich möchte **in wenigen Sekunden** sehen, ob die Combo zu meinem Event passt und wie ich sie erreiche — ohne lange "Über uns"-Texte oder Marketing-Sprech.

## Layout-Konzept

**Desktop (≥ 960px):** Vollbild-Hero mit Auftrittsfoto im Hintergrund (dunkler Overlay #161618 bei 65% Deckkraft). Text linksbündig, vertikal zentriert, max-width 600px. Logo oben links, Nav (Anker-Links zu Sections) oben rechts. Primärer CTA als großer roter Button, sekundärer CTA als Text-Link darunter.

**Mobile (< 960px):** Foto bleibt Hintergrund, Text rückt nach oben (über Logo darunter). CTA-Button ist Full-Width (16px Außen-Padding). Sticky Mobile-Bottom-Bar mit "📞 Jetzt anrufen" als zusätzliche Always-On-CTA.

**Vertikales Padding:** Desktop min. 100vh (Vollbild), Mobile min. 90vh.

## Inhalt (Empfehlung)

**Pre-Headline (Tagline-Strip oben):**
> "Tradition trifft Moderne — Rock, Pop & Blasmusik"

**Headline (H1):**
> "Blasmusik mit Herz 'n Beat."

(Das **N** in "Herz 'n Beat" könnte rot gehighlighted werden — siehe offene Entscheidung 2)

**Subheadline:**
> "Eure Live-Combo aus dem Breisgau — buchbar für Vereinsfeste, Stadtfeste, Hochzeiten und alles, was nach echter Bühne ruft."

**Primary CTA (Button):**
> "📞 Jetzt anrufen: 0171/9900177"
> (`<a href="tel:+4901719900177">` — mobile löst tap-to-call aus)

**Secondary CTA (Text-Link):**
> "Termine ansehen ↓" (Anker zu `#termine`)

**Trust-Strip / Mikro-Text (klein, unter den CTAs):**
> "Folge uns auf Instagram @blech_n_takt · Booking direkt am Telefon"

## Visuelles Element

**Empfehlung:** Großes Auftrittsfoto im Hintergrund — die ganze Combo auf einer Bühne, mit den **roten Schuhen** sichtbar. Aus `~/Desktop/Blech\`N\`Takt /05_Bilder/2024/`. Muss querformat sein (mind. 1920×1080), Personen leicht außermittig (links oder rechts), damit Text-Spalte freibleibt.

**Overlay:** Linearer Gradient von links `#161618` (90%) nach rechts `transparent`, damit Text gut lesbar ist und das Foto trotzdem zur Geltung kommt.

**Logo:** SVG-Version (falls vorhanden) oder PNG — top-left, max-height 64px. Aus `05_Bilder/Logo/`.

## DOM-Struktur

```html
<header class="site-header">
  <a href="/" class="site-header__logo">
    <img src="assets/logo.svg" alt="blech'n'takt — Combo" width="200" height="64">
  </a>
  <nav class="site-header__nav" aria-label="Sektionen">
    <a href="#about">Über uns</a>
    <a href="#videos">Videos</a>
    <a href="#termine">Termine</a>
    <a href="#booking">Booking</a>
  </nav>
</header>

<section class="hero" aria-labelledby="hero-title">
  <div class="hero__bg" aria-hidden="true">
    <img src="assets/photos/hero-live.webp" alt="" loading="eager">
  </div>
  <div class="hero__overlay" aria-hidden="true"></div>
  <div class="hero__content">
    <p class="hero__tagline">Tradition trifft Moderne — Rock, Pop & Blasmusik</p>
    <h1 id="hero-title" class="hero__title">
      Blasmusik mit Herz <span class="red-n">'n</span> Beat.
    </h1>
    <p class="hero__subtitle">
      Eure Live-Combo aus dem Breisgau — buchbar für Vereinsfeste, Stadtfeste,
      Hochzeiten und alles, was nach echter Bühne ruft.
    </p>
    <div class="hero__cta-group">
      <a href="tel:+4901719900177"
         class="btn btn--primary"
         aria-label="Jetzt anrufen für Booking-Anfrage, Telefonnummer 0171 9900177">
        <span aria-hidden="true">📞</span> Jetzt anrufen: 0171/9900177
      </a>
      <a href="#termine" class="hero__secondary-link">Termine ansehen ↓</a>
    </div>
    <p class="hero__microtrust">
      Folge uns auf Instagram <a href="https://instagram.com/blech_n_takt">@blech_<span class="red-n">n</span>_takt</a>
      · Booking direkt am Telefon
    </p>
  </div>
</section>

<a href="tel:+4901719900177" class="sticky-call" aria-label="Jetzt anrufen">
  <span aria-hidden="true">📞</span> Anrufen
</a>
```

## Stile

| Element | Spezifikation |
|---|---|
| Hero `<section>` | `min-height: 100vh` Desktop / `90vh` Mobile, `background: #161618`, `color: #fff` |
| `.hero__bg img` | `position: absolute, inset: 0, width: 100%, height: 100%, object-fit: cover, object-position: center` |
| `.hero__overlay` | linearer Gradient `to right, rgba(22,22,24,.92), rgba(22,22,24,.55) 60%, rgba(22,22,24,.4)` |
| `.hero__tagline` | Inter 600, 16px Desktop / 14px Mobile, letter-spacing 2px, uppercase, color `#B22325` |
| `.hero__title` (H1) | Inter 900, **clamp(40px, 6vw, 80px)**, line-height 1.05, color `#fff` |
| `.red-n` | color `#B22325` (Brand-Konstante) |
| `.hero__subtitle` | Inter 400, 18px Desktop / 16px Mobile, line-height 1.5, color `rgba(255,255,255,.85)`, max-width 580px |
| `.btn--primary` | bg `#B22325`, color `#fff`, padding `18px 32px`, font-weight 700, border-radius 8px, font-size 18px, **min-height 56px** (touch-target) |
| `.btn--primary:hover` | bg `#9a1d1f` (10% dunkler), transform `translateY(-1px)`, transition 0.2s |
| `.hero__secondary-link` | color `rgba(255,255,255,.7)`, underline on hover, 16px |
| `.sticky-call` | position fixed bottom 0, full-width Mobile only, bg `#B22325`, color `#fff`, padding 16px, **z-index 100** |

## Verhalten

- **Sticky-Call-Button** nur auf Mobile (< 720px) sichtbar — verschwindet auf Desktop
- **Anker-Links** (`#about`, `#videos`, `#termine`) → smooth scroll via `scroll-behavior: smooth` auf `<html>`
- **Hover-States** nur für interaktive Elemente (CTA, Links)
- **Focus-Visible:** 2px Outline `#B22325` mit 2px Offset auf alle interaktiven Elemente
- **`@media (prefers-reduced-motion: reduce)`**: alle Transitions auf 0.001ms, smooth-scroll deaktivieren
- **Kein Auto-Play** (gibt es hier eh nicht — Hero-Foto ist statisch)

## Akzeptanzkriterien

- [ ] Headline und CTA in ≤ 5 Sekunden erfassbar (Squint-Test bestehen)
- [ ] Tel-Button auf Mobile-Tap löst Anruf-Dialog aus (iOS Safari + Android Chrome getestet)
- [ ] Above-the-fold auf MacBook 13" (1280×800) und iPhone SE (375×667) komplett sichtbar
- [ ] Lesbar bei 320px Viewport (kleinster Mobile-Test)
- [ ] WCAG-AA-Kontrast: Headline `#fff` auf Overlay (≥ 7:1), Subline `rgba(255,255,255,.85)` (≥ 4.5:1)
- [ ] Funktioniert ohne JavaScript (kein JS im Hero zwingend nötig)
- [ ] Keyboard-Navigation: Tab → Logo → Nav-Links → Tel-CTA → Termine-Link
- [ ] Sticky-Call-Bar nur auf Mobile, überlappt keinen wichtigen Content
- [ ] Reduced-Motion: keine Animationen
- [ ] Hero-Foto lädt < 100 KB (WebP komprimiert)

## Offene Entscheidungen (brauchen Freigabe)

### 1. Hero-Foto: Welches?

| # | Variante | Wo gefunden | Charakter |
|---|---|---|---|
| **A** ★ | **Bühnen-Vollbild mit ganzer Combo** | Aus `05_Bilder/2024/` — bestes querformatiges Auftrittsfoto | Atmosphärisch, Live-Beweis sofort, rote Schuhe sichtbar |
| B | **Comic-Logo aus Logo-Ordner** | `blech´n´takt_Comic-1-.jpg` | Verspielt, ikonisch, schnellladend — aber zeigt keine echten Personen |
| C | **Roll-Up-Banner-Motiv** | `blech´n´takt (Roll Up Banner).pdf` | Klar, brand-konform — aber statisch, weniger emotional |

**Empfehlung A** — du müsstest mir sagen, welches Foto aus `05_Bilder/2024/` das beste ist (oder ich schau mir mal alle an und schlage 2–3 Kandidaten vor).

### 2. Headline-Variante

| # | Variante | Charakter |
|---|---|---|
| **A** ★ | "Blasmusik mit Herz 'n Beat." | Direkt aus dem Brand-Slogan, kurz, einprägsam |
| B | "Tradition trifft Moderne — live auf eurer Bühne." | Klassischer, mehr "Booker-Ansprache" |
| C | "Rock, Pop & Blech. Live." | Knapp, aktivierend, fokussiert auf Genres |

### 3. Sticky-Mobile-Call-Button: Ja oder nein?

| # | Variante | Charakter |
|---|---|---|
| **A** ★ | **Ja, immer sichtbar** | Maximale Conversion — Tel-Button nie weg vom Daumen |
| B | Nein, nur im Hero und Footer | Schlanker, aber Booker muss scrollen oder zurück |

## Tonalitäts-Reminder (aus CLAUDE.md)

- Du-Form, locker, kein Marketing-Sprech
- Kein "wir bieten Ihnen", kein "professionelle Live-Unterhaltung"
- Sprache wie aus `07_Marketing/Info_Material/blech´n´takt Info.docx`
