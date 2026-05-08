# Feature 004 — Galerie

**Status:** Entwurf
**Erstellt:** 2026-05-08

---

## Ziel

"Wie sehen die aus, wie ist die Stimmung?" — 4–6 Fotos aus echten Auftritten als Grid. Keine gestellten Fotos, keine Stockbilder.

## Layout-Konzept

**Desktop (≥ 1100px):** 4 Spalten Grid, ungleiche Höhen erlaubt (Masonry-Light via `grid-auto-rows`).
**Tablet (720–1100px):** 3 Spalten.
**Mobile (< 720px):** 2 Spalten.

Padding 96px Desktop / 64px Mobile.

## Inhalt

**Section-Headline:**
> "Auf der Bühne."

**Subline (klein, optional):**
> "Eindrücke aus unseren letzten Auftritten."

**Fotos (initialer Vorschlag aus 05_Bilder):**

1. IMG_5441 — Bühnen-Komplettansicht (falls nicht schon Hero)
2. IMG_5435 — Selfie-Group mit grünem Licht
3. IMG_5495 — Selfie aus anderer Location
4. IMG_5496 — Variante davon
5. IMG_5436 — Variante davon
6. (optional weitere, vom User geliefert)

## DOM-Struktur

```html
<section class="gallery" id="galerie" aria-labelledby="gallery-title">
  <div class="gallery__container">
    <h2 id="gallery-title" class="section-title">Auf der Bühne.</h2>
    <p class="gallery__subtitle">Eindrücke aus unseren letzten Auftritten.</p>
    <ul class="gallery__grid" role="list">
      <li>
        <figure class="gallery__item">
          <img src="assets/photos/gallery-01.webp"
               alt="blech'n'takt live im Festzelt, Trompeten am Mund"
               loading="lazy" width="800" height="600">
        </figure>
      </li>
      <!-- 3-5 weitere -->
    </ul>
  </div>
</section>
```

## Stile

| Element | Spezifikation |
|---|---|
| `.gallery` | bg `#161618`, padding `96px 24px` |
| `.gallery__grid` | display grid, gap 16px, list-style none, padding 0 |
| `.gallery__grid` (Mobile) | `grid-template-columns: repeat(2, 1fr)` |
| `.gallery__grid` (≥ 720px) | `repeat(3, 1fr)` |
| `.gallery__grid` (≥ 1100px) | `repeat(4, 1fr)` |
| `.gallery__item img` | width 100%, height 100%, object-fit cover, border-radius 8px, transition transform 0.3s |
| `.gallery__item:hover img` | transform scale(1.03) — nur auf Hover-Geräten via `@media (hover: hover)` |

## Verhalten

- **Lazy-Loading** zwingend (`loading="lazy"`) — Galerie ist weit unten in der Page
- **Kein Lightbox** in Phase 5 (Bilder als reines Grid). Optional in Phase 6 nachrüsten.
- **Reduced-Motion:** kein Scale-Hover

## Akzeptanzkriterien

- [ ] Mindestens 4 Fotos sichtbar
- [ ] Keine Stockfotos
- [ ] Alt-Texte: aussagekräftig (nicht "Foto1")
- [ ] Mobile (320px): Grid funktioniert, kein horizontales Scrollen
- [ ] Bilder lazy-loaded, einzeln max 80 KB nach Komprimierung

## Offene Entscheidungen

### 1. Lightbox bei Klick?

| # | Variante | Charakter |
|---|---|---|
| **A** ★ | Kein Lightbox in v1, kann später nachgerüstet werden | Schlanker Start, weniger JS |
| B | Lightbox direkt | Mehr Polish, aber zusätzliche JS-Komplexität |

### 2. Welche Fotos genau?

User muss finale Auswahl liefern (siehe Hero-Foto-Suche).
