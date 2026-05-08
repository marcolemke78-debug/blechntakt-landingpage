# Feature 003 — Live-Videos

**Status:** Entwurf
**Erstellt:** 2026-05-08

---

## Ziel

Beweis "wie klingen die": **2–3 Instagram-Reels eingebettet**. Ohne dieses visuelle Vertrauenssignal entscheidet kein Booker. Reels sind eingebunden, aber nicht auto-play.

## Layout-Konzept

**Desktop (≥ 960px):** Drei Reels nebeneinander im Grid (3 Spalten, gap 24px). Reels haben Hochformat (9:16), passen gut nebeneinander.

**Mobile (< 960px):** Stacked, ein Reel pro Reihe. Carousel/Swipe optional, aber nicht Pflicht.

## Inhalt

**Section-Headline:**
> "Wie klingt das live?"

**Subline:**
> "Drei kurze Eindrücke direkt von unserem Instagram. Klick zum Abspielen."

**Embed-Methode:** Instagram **Blockquote-Embed** mit Lazy-Skript-Loading. Kein Auto-Play, kein Tracking, bevor User klickt.

```html
<blockquote class="instagram-media"
            data-instgrm-permalink="https://www.instagram.com/reel/REEL_ID_HIER/"
            data-instgrm-version="14">
</blockquote>
```

Nach dem User-Klick wird Insta-Skript dynamisch geladen (siehe Verhalten unten).

**CTA unter den Reels:**
> "Mehr auf Instagram → @blech_n_takt"

## DOM-Struktur

```html
<section class="videos" id="videos" aria-labelledby="videos-title">
  <div class="videos__container">
    <h2 id="videos-title" class="section-title">Wie klingt das live?</h2>
    <p class="videos__subtitle">
      Drei kurze Eindrücke direkt von unserem Instagram. Klick zum Abspielen.
    </p>
    <div class="videos__grid">
      <article class="reel-card">
        <a class="reel-card__placeholder"
           href="https://www.instagram.com/reel/REEL_ID_1/"
           data-reel-id="REEL_ID_1">
          <img src="assets/photos/reel-thumb-1.webp"
               alt="Vorschau Reel 1: Auftritt beim Glotterfest"
               loading="lazy" width="400" height="711">
          <span class="reel-card__play" aria-hidden="true">▶</span>
        </a>
        <p class="reel-card__caption">Glotterfest Nimburg 2025</p>
      </article>
      <!-- 2 weitere Reels analog -->
    </div>
    <a class="videos__more" href="https://instagram.com/blech_n_takt" rel="noopener">
      Mehr auf Instagram → @blech_<span class="red-n">n</span>_takt
    </a>
  </div>
</section>
```

## Verhalten

- **Klick auf Placeholder** → Instagram-Embed-Skript wird dynamisch geladen, Reel ersetzt Placeholder im Card
- **Vor Klick** = nur Bild + Play-Icon = 0 KB Drittanbieter-Code = DSGVO-freundlich
- **Lazy-Loading** für Thumbnails

## Stile

| Element | Spezifikation |
|---|---|
| `.videos` | bg `#0c0c0e` (etwas dunkler als Body), padding `96px 24px` |
| `.videos__grid` | display grid, `repeat(3, 1fr)` Desktop / `1fr` Mobile, gap 24px |
| `.reel-card__placeholder` | aspect-ratio 9/16, border-radius 12px, overflow hidden, position relative |
| `.reel-card__play` | position absolute, center, font-size 48px, color `#fff`, bg `rgba(178,35,37,.9)`, w/h 80px, border-radius 50%, display flex, align/justify center |
| `.reel-card__placeholder:hover .reel-card__play` | transform scale(1.1), bg `#B22325`, transition 0.2s |

## Akzeptanzkriterien

- [ ] Page lädt OHNE Insta-Skript zunächst (DSGVO-Freundlichkeit)
- [ ] Reel-Thumbnails sind lazy-loaded
- [ ] Klick lädt Embed-Skript und spielt Reel ab
- [ ] Reduced-Motion: keine Hover-Animationen
- [ ] Funktioniert auch ohne JavaScript (fällt zurück auf reinen Link zu Instagram)
- [ ] Mobile: Tap auf Reel funktioniert direkt

## Offene Entscheidungen

### 1. Welche 3 Reels?

User muss die Reel-IDs/URLs liefern. Empfehlung: Drei verschiedene Stilrichtungen — z. B. ein Pop-Cover, ein Marsch, ein Stimmungs-Cut. Maximal 60 Sekunden pro Reel.

### 2. Klick-zu-Embed oder direkt zu Instagram?

| # | Variante | Charakter |
|---|---|---|
| **A** ★ | Klick → Embed inline, bleibt auf Page | Mehr Verweildauer, Funnel intakt |
| B | Klick → öffnet Insta direkt (neuer Tab) | Schlanker, aber User verlässt Page |
