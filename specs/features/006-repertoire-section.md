# Feature 006 — Repertoire-Auszug

**Status:** Entwurf
**Erstellt:** 2026-05-08

---

## Ziel

"Spielen die das, was bei meinem Event passt?" — typische Booker-Frage. Wir zeigen einen **Auszug** (8–12 Highlights, nicht die komplette 100+-Liste), gegliedert in Genre-Kategorien.

Quelle: `~/Desktop/Blech\`N\`Takt /02_Repertoire/Aktuell/Repertoire 2026 B´n´T.pdf`

## Layout-Konzept

**Desktop (≥ 720px):** Drei Spalten Grid (eine Spalte pro Kategorie).
**Mobile (< 720px):** 1 Spalte, gestackt.

Padding 96px Desktop / 64px Mobile.

## Inhalt

**Section-Headline:**
> "Was wir spielen — ein Auszug."

**Subline:**
> "Über 100 Songs im Programm. Hier eine kleine Kostprobe."

**Drei Kategorien (Beispiel — finale Auswahl liefert User):**

| 🎺 Klassiker | 🎸 Pop & Rock | 🍻 Stimmung |
|---|---|---|
| Böhmischer Traum | Skyfall (Adele) | Atemlos |
| Schneewalzer | Sweet Caroline | Cordula Grün |
| Egerländer | Don't Stop Me Now | Ein Stern |
| In München steht ein Hofbräuhaus | Uptown Funk | Westerland |

**CTA am Ende:**
> "Vermisst du was? **Frag uns — wir lernen vieles dazu.** 📞 0171/9900177"

## DOM-Struktur

```html
<section class="repertoire" id="repertoire" aria-labelledby="rep-title">
  <div class="repertoire__container">
    <h2 id="rep-title" class="section-title">Was wir spielen — ein Auszug.</h2>
    <p class="repertoire__subtitle">Über 100 Songs im Programm. Hier eine kleine Kostprobe.</p>

    <div class="repertoire__grid">
      <div class="rep-cat">
        <h3 class="rep-cat__title"><span aria-hidden="true">🎺</span> Klassiker</h3>
        <ul class="rep-cat__list">
          <li>Böhmischer Traum</li>
          <li>Schneewalzer</li>
          <!-- 2-4 weitere -->
        </ul>
      </div>
      <div class="rep-cat">
        <h3 class="rep-cat__title"><span aria-hidden="true">🎸</span> Pop & Rock</h3>
        <ul class="rep-cat__list">
          <li>Skyfall</li>
          <!-- ... -->
        </ul>
      </div>
      <div class="rep-cat">
        <h3 class="rep-cat__title"><span aria-hidden="true">🍻</span> Stimmung</h3>
        <ul class="rep-cat__list">
          <li>Atemlos</li>
          <!-- ... -->
        </ul>
      </div>
    </div>

    <p class="repertoire__cta">
      Vermisst du was? <strong>Frag uns — wir lernen vieles dazu.</strong>
      <a href="tel:+4901719900177">📞 0171/9900177</a>
    </p>
  </div>
</section>
```

## Stile

| Element | Spezifikation |
|---|---|
| `.repertoire` | bg `#161618`, padding `96px 24px` |
| `.repertoire__grid` | display grid, `1fr` Mobile / `repeat(3, 1fr)` Desktop, gap 32px |
| `.rep-cat` | padding 24px, border-radius 12px, border `1px solid rgba(255,255,255,.08)` |
| `.rep-cat__title` | Inter 700, 20px, color `#B22325`, margin-bottom 16px, display flex, gap 12px, align-items center |
| `.rep-cat__list` | list-style none, padding 0 |
| `.rep-cat__list li` | padding 10px 0, border-bottom `1px solid rgba(255,255,255,.06)`, color `rgba(255,255,255,.85)` |

## Akzeptanzkriterien

- [ ] Maximal 12 Songs gesamt (4 pro Kategorie)
- [ ] Drei Kategorien decken die Bandbreite ab (nicht nur Stimmung, nicht nur Pop)
- [ ] Mobile: Listen lesbar, kein hässlicher Umbruch
- [ ] CTA unten verlinkt zu Tel

## Offene Entscheidungen

### 1. Welche 12 Songs konkret?

User wählt aus dem Repertoire-PDF aus. Kriterium: Bekannte Songs, die einen Veranstalter sofort einordnen lassen ("ah, die spielen das").

### 2. Sollen wir die volle Liste als PDF-Download anbieten?

| # | Variante | Charakter |
|---|---|---|
| **A** ★ | Nein, keine PDF-Download — Liste auf Anfrage | Schlanker, kein PDF-Hosting |
| B | Ja, PDF im Footer verlinkt | Service-orientiert, aber öffentlich verfügbar |
