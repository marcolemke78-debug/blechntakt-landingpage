# Feature 002 — Über uns

**Status:** Entwurf
**Erstellt:** 2026-05-08

---

## Ziel

Vertrauen aufbauen: "Wer ist diese Combo, was macht sie aus, ist sie für mein Event passend?" — basierend auf eurem Info-Doc (`07_Marketing/Info_Material/blech´n´takt Info.docx`).

## Layout-Konzept

**Desktop (≥ 960px):** Zwei Spalten, links Text (60%), rechts ein vertikales Foto/Detailbild (40%) — z. B. ein Selfie aus der Galerie oder das Logo-Comic. Vertikales Padding 96px.

**Mobile (< 960px):** Stacked. Foto unter dem Text, Padding 64px.

## Inhalt

**Section-Headline:**
> "Tradition trifft Moderne — live auf eurer Bühne."

**Lead-Absatz (gekürzt aus dem Info-Doc):**
> "Wir sind blech'n'takt — eine Blech-Combo mit Schlagzeug aus dem Breisgau. Drei Trompeten, Posaune, Euphonium, Tuba und Drums. Zusammen bringen wir das, was viele ankündigen und wenige liefern: satten Blech-Sound, der nicht im Festzelt verhallt, sondern groovt."

**Was uns ausmacht (3 kurze Punkte mit Icons):**

| Icon | Punkt |
|---|---|
| 🎺 | **Echte Live-Combo** — keine Konserven, keine Half-Playback-Tricks. Sieben Musiker, sieben Instrumente, ein Schlagzeug. |
| 🎬 | **Show mit Zug** — überwiegend im Sitzen für stabiles Timing, gezielte Highlights durch gemeinsames Aufstehen. Moderation vom Platz. |
| 👞 | **Erkennbar** — schwarzer Look, Hosenträger und unsere roten Schuhe als Markenzeichen. |

**Wo wir spielen (Mini-Liste):**
> Vereinsfeste · Stadtfeste · Hallenabende · Open-Air-Sets · Hochzeiten · kulinarische Feste

## DOM-Struktur

```html
<section class="about" id="about" aria-labelledby="about-title">
  <div class="about__container">
    <div class="about__text">
      <h2 id="about-title" class="section-title">
        Tradition trifft Moderne — <br>
        <span class="accent">live auf eurer Bühne.</span>
      </h2>
      <p class="about__lead">Wir sind blech'<span class="red-n">n</span>'takt …</p>
      <ul class="about__points">
        <li><span class="about__icon" aria-hidden="true">🎺</span>
          <strong>Echte Live-Combo</strong> — keine Konserven …</li>
        <li><span class="about__icon" aria-hidden="true">🎬</span>
          <strong>Show mit Zug</strong> — überwiegend im Sitzen …</li>
        <li><span class="about__icon" aria-hidden="true">👞</span>
          <strong>Erkennbar</strong> — schwarzer Look, Hosenträger …</li>
      </ul>
      <p class="about__events"><strong>Wo wir spielen:</strong>
        Vereinsfeste · Stadtfeste · Hallenabende · Open-Air-Sets · Hochzeiten · kulinarische Feste</p>
    </div>
    <figure class="about__media">
      <img src="assets/photos/about-portrait.webp"
           alt="Die Combo blech'n'takt im typischen schwarzen Look mit roten Schuhen"
           loading="lazy" width="600" height="800">
    </figure>
  </div>
</section>
```

## Stile

| Element | Spezifikation |
|---|---|
| `.about` | bg `#161618`, padding `96px 24px` Desktop / `64px 16px` Mobile |
| `.about__container` | max-width 1200px, mx auto, grid `1fr` Mobile / `3fr 2fr` Desktop, gap 64px |
| `.section-title` (H2) | Inter 800, clamp(32px, 4.5vw, 56px), line-height 1.1, color `#fff` |
| `.section-title .accent` | color `#B22325` |
| `.about__lead` | Inter 400, 18px, line-height 1.6, color `rgba(255,255,255,.85)` |
| `.about__points li` | display flex, gap 16px, padding 12px 0, border-bottom `1px solid rgba(255,255,255,.1)` |
| `.about__icon` | font-size 28px, flex-shrink 0 |
| `.about__media img` | width 100%, border-radius 12px, object-fit cover |

## Akzeptanzkriterien

- [ ] Lead-Absatz erfasst Combo-Charakter in 1–2 Sätzen
- [ ] Drei Punkte fassen das USP klar zusammen
- [ ] WCAG-AA-Kontrast eingehalten
- [ ] Foto lädt lazy, max 80 KB
- [ ] Bei 320px Viewport lesbar, Liste bricht nicht hässlich um

## Offene Entscheidungen

### 1. Welches Foto rechts?

| # | Variante | Charakter |
|---|---|---|
| **A** ★ | Selfie aus 5435/5436 (alle lachen, Hosenträger sichtbar) | Sympathisch, nahbar |
| B | Logo-Comic (`blech´n´takt_Comic-1-.jpg`) | Brand-konform, aber distanziert |
| C | Kein Foto, nur Text-Spalte breiter | Schlanker, aber visuell langweilig |
