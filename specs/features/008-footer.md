# Feature 008 — Footer

**Status:** Entwurf
**Erstellt:** 2026-05-08

---

## Ziel

Rechtlicher Abschluss + Last-Touch-Branding. Pflicht: Impressum + Datenschutz. Plus dezent: Logo, Tagline, Copyright.

## Layout-Konzept

**Desktop:** Drei Spalten — links Logo + Tagline, mittig Insta/FB-Links, rechts Impressum/Datenschutz-Links.
**Mobile:** Stacked.

Padding 64px oben/unten Desktop, 48px Mobile. Border-top als feine Linie zur Booking-Section.

## Inhalt

**Logo-Spalte (links):**
- Mini-Logo (max-height 48px)
- Tagline: "Follow the Takt!"
- Copyright: "© 2026 blech'n'takt"

**Social-Spalte (mittig):**
- Instagram: @blech_n_takt
- Facebook: bit.ly/FB_blechtakt

**Legal-Spalte (rechts):**
- Impressum (→ `impressum.html`)
- Datenschutz (→ `datenschutz.html`)

## DOM-Struktur

```html
<footer class="site-footer">
  <div class="site-footer__container">
    <div class="site-footer__brand">
      <img src="assets/logo.svg" alt="blech'n'takt" width="120" height="48">
      <p class="site-footer__tagline">Follow the Takt!</p>
      <p class="site-footer__copy">© 2026 blech'<span class="red-n">n</span>'takt</p>
    </div>

    <nav class="site-footer__social" aria-label="Social Media">
      <a href="https://instagram.com/blech_n_takt" rel="noopener">
        <span aria-hidden="true">📷</span> Instagram
      </a>
      <a href="https://bit.ly/FB_blechtakt" rel="noopener">
        <span aria-hidden="true">f</span> Facebook
      </a>
    </nav>

    <nav class="site-footer__legal" aria-label="Rechtliches">
      <a href="impressum.html">Impressum</a>
      <a href="datenschutz.html">Datenschutz</a>
    </nav>
  </div>
</footer>
```

## Stile

| Element | Spezifikation |
|---|---|
| `.site-footer` | bg `#0a0a0c`, color `rgba(255,255,255,.5)`, padding `64px 24px` Desktop / `48px 16px` Mobile, border-top `1px solid rgba(255,255,255,.08)` |
| `.site-footer__container` | max-width 1200px, mx auto, display grid, `1fr` Mobile / `repeat(3, 1fr)` Desktop, gap 32px, align-items start |
| `.site-footer__brand img` | max-height 48px, opacity 0.8 |
| `.site-footer__tagline` | letter-spacing 2px, text-transform uppercase, font-size 14px, font-weight 600, margin-top 12px |
| `.site-footer__copy` | font-size 12px, margin-top 8px, opacity 0.6 |
| `.site-footer__social a, .site-footer__legal a` | color `rgba(255,255,255,.6)`, text-decoration none, display block, padding 6px 0, font-size 14px |
| `.site-footer__social a:hover, .site-footer__legal a:hover` | color `#B22325` |

## Akzeptanzkriterien

- [ ] Impressum-Link erreichbar (auch wenn Seite noch leer)
- [ ] Datenschutz-Link erreichbar
- [ ] WCAG-AA-Kontrast (4.5:1 für die kleine Schrift auf dunklem Hintergrund)
- [ ] Mobile: alle Links Touch-tauglich (min 44px Tap-Höhe)
- [ ] Externe Links mit `rel="noopener"`

## Zusatz: impressum.html und datenschutz.html

Diese Seiten werden in Phase 5 minimal angelegt:

**impressum.html** (Standard-Inhalt):
- Anbieter (User liefert: Name, Adresse, Email)
- Kontakt (Tel, Mail)
- Haftungshinweis (Standard-Text)

**datenschutz.html** (Standard-Inhalt für statische Page ohne Tracker):
- Verantwortlicher
- Server-Logfiles (falls GitHub Pages → siehe deren Datenschutz-Erklärung verlinken)
- Externe Inhalte: Instagram-Embeds, Google Fonts (Hinweis dass beim Klicken Daten an Drittanbieter gehen)
- Keine Cookies, keine Analytics

## Offene Entscheidungen

### 1. Impressums-Daten

User liefert in Phase 5:
- Vor- und Nachname (oder Vereinsname falls Verein)
- Ladungsfähige Adresse
- E-Mail-Kontakt
- Falls Verein: Vereinsregister-Nr.

### 2. Google Fonts lokal hosten oder via CDN?

| # | Variante | Charakter |
|---|---|---|
| **A** ★ | Lokal hosten (Inter selbst-gehostet) | DSGVO-konform ohne Hinweise, schneller |
| B | Via Google CDN | Einfacher, aber Datenschutz-Hinweis nötig |
