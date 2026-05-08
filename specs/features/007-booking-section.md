# Feature 007 — Booking-Block (Final-CTA)

**Status:** Entwurf
**Erstellt:** 2026-05-08

---

## Ziel

**Letzter Conversion-Punkt vor dem Footer.** Wer bis hier gescrollt hat, ist warm. Großer, prominenter Booking-Block mit Tel-CTA — kein Formular, kein Friction.

## Layout-Konzept

**Vollbreiter Block** mit dunklem Brand-Rot-Hintergrund (`#B22325`) als visueller Kontrast zur restlichen schwarzen Page. Text zentriert, max-width 800px, vertikal gepolstert.

**Desktop:** Padding 120px oben/unten.
**Mobile:** Padding 80px oben/unten.

## Inhalt

**Pre-Headline:**
> "Bühne frei für euch."

**Headline (groß):**
> "Lass uns reden. 📞"

**Lead-Text:**
> "Ein Anruf reicht. Wir besprechen dein Event, klären Datum und Setup, und sagen dir ehrlich, ob wir passen — oder dir jemand anderen empfehlen."

**Primary CTA:**
> "📞 0171/9900177" (sehr groß, weißer Button auf rotem Hintergrund)

**Sekundär (klein darunter):**
> "Erreichbar Mo–Fr 18–21 Uhr · Sa/So nach Auftritten"

**Kontakt-Alternativen (Icon-Liste, klein):**

- Instagram: @blech_n_takt
- Facebook: bit.ly/FB_blechtakt

## DOM-Struktur

```html
<section class="booking" id="booking" aria-labelledby="booking-title">
  <div class="booking__container">
    <p class="booking__pre">Bühne frei für euch.</p>
    <h2 id="booking-title" class="booking__title">Lass uns reden. <span aria-hidden="true">📞</span></h2>
    <p class="booking__lead">
      Ein Anruf reicht. Wir besprechen dein Event, klären Datum und Setup, und
      sagen dir ehrlich, ob wir passen — oder dir jemand anderen empfehlen.
    </p>
    <a href="tel:+4901719900177" class="booking__cta-tel"
       aria-label="Anrufen unter 0171 9900177">
      <span aria-hidden="true">📞</span> 0171/9900177
    </a>
    <p class="booking__hours">Erreichbar Mo–Fr 18–21 Uhr · Sa/So nach Auftritten</p>
    <ul class="booking__alt" role="list">
      <li><a href="https://instagram.com/blech_n_takt" rel="noopener">
        <span aria-hidden="true">📷</span> Instagram @blech_<span class="red-n-on-red">n</span>_takt
      </a></li>
      <li><a href="https://bit.ly/FB_blechtakt" rel="noopener">
        <span aria-hidden="true">f</span> Facebook
      </a></li>
    </ul>
  </div>
</section>
```

## Stile

| Element | Spezifikation |
|---|---|
| `.booking` | bg `#B22325`, color `#fff`, padding `120px 24px` Desktop / `80px 16px` Mobile, text-align center |
| `.booking__container` | max-width 800px, mx auto |
| `.booking__pre` | Inter 600, 16px, letter-spacing 3px, uppercase, opacity 0.8 |
| `.booking__title` | Inter 900, clamp(40px, 6vw, 72px), line-height 1.05, margin 16px 0 24px |
| `.booking__lead` | font-size 18px, line-height 1.6, opacity 0.95, margin-bottom 40px |
| `.booking__cta-tel` | display inline-block, bg `#fff`, color `#B22325`, padding `24px 40px`, font-size 32px, font-weight 900, border-radius 12px, text-decoration none, min-height 72px |
| `.booking__cta-tel:hover` | bg `#161618`, color `#fff`, transition 0.2s |
| `.booking__hours` | margin-top 16px, font-size 14px, opacity 0.8 |
| `.booking__alt` | margin-top 40px, display flex, gap 32px, justify-content center, list-style none, padding 0, flex-wrap wrap |
| `.booking__alt a` | color `#fff`, text-decoration underline, opacity 0.9 |
| `.red-n-on-red` | color `#161618` (auf rotem Hintergrund umgekehrt) |

## Akzeptanzkriterien

- [ ] Tel-CTA ist visuell der größte Button auf der gesamten Page
- [ ] Auf Mobile: Tap löst Anruf-Dialog aus
- [ ] WCAG-AA-Kontrast: weißer Text auf `#B22325` (≥ 4.5:1) ✓
- [ ] Sekundäre Links (Insta, FB) öffnen in neuem Tab (`rel="noopener"`)
- [ ] Reduced-Motion: keine Hover-Animationen

## Offene Entscheidungen

### 1. Telefonzeiten korrekt?

User bestätigt oder korrigiert "Mo–Fr 18–21 Uhr · Sa/So nach Auftritten". Falls keine festen Zeiten gewünscht: weglassen.

### 2. WhatsApp als zusätzliche Alternative?

| # | Variante | Charakter |
|---|---|---|
| A | Nur Tel + Insta + FB | Konsequent: Anrufen ist Hauptweg |
| **B** ★ | Tel + WhatsApp-Link + Insta + FB | Zusätzliche niedrigschwellige Option für Junge / asynchrone Kommunikation |
