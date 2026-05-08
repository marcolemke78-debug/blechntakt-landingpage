# Feature 005 — Termine 2026

**Status:** Entwurf
**Erstellt:** 2026-05-08

---

## Ziel

"Die spielen aktiv und regelmäßig" — soziales Vertrauenssignal Nr. 1 für Booker. Plus: Fans erfahren, wo sie euch live sehen können.

Quelle: `~/Desktop/Blech\`N\`Takt /06_Verwaltung/Termine/Termine 2026.xlsx`

## Layout-Konzept

**Desktop (≥ 960px):** Termin-Karten im 2-Spalten-Grid (gap 24px). Aktuelle/zukünftige Termine oben, vergangene ausgegraut darunter (oder per Toggle ausgeblendet).

**Mobile (< 960px):** 1 Spalte, gestackt.

## Inhalt

**Section-Headline:**
> "Hier spielen wir 2026."

**Subline:**
> "Komm vorbei oder bring uns zu deiner Bühne."

**Termin-Karte (Vorlage):**

```
┌────────────────────────────────┐
│ FR · 27.06.2026 · 19:00 Uhr   │ ← Datum-Strip oben (CSS_ROT)
│                                │
│ Glotterfest Nimburg            │ ← Event-Name (groß, weiß)
│ 📍 Festplatz Nimburg           │ ← Ort (klein, gedämpft)
│                                │
│ Bestätigt ✓                    │ ← Badge (grün)
└────────────────────────────────┘
```

**CTA am Ende (klein):**
> "Du willst uns auf eine Bühne holen? **📞 Anrufen: 0171/9900177**"

## DOM-Struktur

```html
<section class="gigs" id="termine" aria-labelledby="gigs-title">
  <div class="gigs__container">
    <h2 id="gigs-title" class="section-title">Hier spielen wir 2026.</h2>
    <p class="gigs__subtitle">Komm vorbei oder bring uns zu deiner Bühne.</p>

    <ul class="gigs__list" role="list">
      <li class="gig-card">
        <div class="gig-card__date">
          <span class="gig-card__weekday">FR</span>
          <span class="gig-card__day">27.06.2026</span>
          <span class="gig-card__time">19:00 Uhr</span>
        </div>
        <h3 class="gig-card__title">Glotterfest Nimburg</h3>
        <p class="gig-card__venue">📍 Festplatz Nimburg</p>
        <span class="gig-card__badge gig-card__badge--confirmed">Bestätigt ✓</span>
      </li>
      <!-- weitere Termine analog -->
    </ul>

    <p class="gigs__cta">
      Du willst uns auf eine Bühne holen?
      <a href="tel:+4901719900177" class="gigs__cta-link">📞 Anrufen: 0171/9900177</a>
    </p>
  </div>
</section>
```

## Stile

| Element | Spezifikation |
|---|---|
| `.gigs` | bg `#0c0c0e`, padding `96px 24px` |
| `.gigs__list` | display grid, `1fr` Mobile / `repeat(2, 1fr)` Desktop, gap 24px |
| `.gig-card` | bg `#1c1c1f`, border `1px solid rgba(255,255,255,.08)`, border-radius 12px, padding 24px |
| `.gig-card__date` | display flex, gap 12px, color `#B22325`, font-weight 700, font-size 14px, letter-spacing 1px, uppercase, margin-bottom 12px |
| `.gig-card__title` | Inter 800, 24px, color `#fff`, margin-bottom 8px |
| `.gig-card__venue` | color `rgba(255,255,255,.6)`, font-size 16px |
| `.gig-card__badge--confirmed` | bg `rgba(34,197,94,.15)`, color `#22C55E`, padding 4px 10px, border-radius 4px, font-size 12px, display inline-block, margin-top 12px |
| `.gig-card__badge--tentative` | bg `rgba(255,193,7,.15)`, color `#FFC107` (für unbestätigte) |
| `.gig-card--past` | opacity 0.5 |

## Akzeptanzkriterien

- [ ] Termine sortiert nach Datum aufsteigend (vergangene zuletzt oder ausgeblendet)
- [ ] Vergangene Termine optisch unterschieden (opacity 0.5)
- [ ] Bestätigt/unbestätigt visuell erkennbar
- [ ] Karten klickbar wenn weiterführender Link existiert (sonst statisch)
- [ ] Mobile: Karten mit ausreichend Padding für Touch (min 44px Höhe für klickbare Elemente)

## Offene Entscheidungen

### 1. Termin-Daten

User liefert die Termine 2026 — entweder als CSV-Export aus der xlsx oder als handgeschriebene Liste. Format pro Termin: Datum + Uhrzeit + Event-Name + Ort + Status (bestätigt/unbestätigt).

### 2. Vergangene Termine zeigen oder ausblenden?

| # | Variante | Charakter |
|---|---|---|
| **A** ★ | Vergangene ausgegraut zeigen | Beweist Aktivität, "die spielen wirklich" |
| B | Nur zukünftige zeigen | Schlanker, fokussierter |
