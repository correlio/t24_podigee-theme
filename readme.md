# tankpool24 – Podigee Webplayer Theme

Custom Podigee webplayer theme for den tankpool24-Podcast, gebaut auf Basis des
[podigee-podcast-player-theme-sdk](https://github.com/podigee/podigee-podcast-player-theme-sdk).

Farben und Formsprache orientieren sich an der tankpool24-Marke
(`#e53533` Rot, dezent abgerundete Ecken statt der verspielteren
15px-Rundungen des Standard-Themes) – siehe [tankpool24.eu](https://www.tankpool24.eu/).

## Struktur

- `themes/tankpool24/index.html` – Player-Markup (unverändert vom Standard-Theme)
- `themes/tankpool24/index.css` – Styling mit tankpool24-Farben (Variablen in `:root`)
- `podcast.json` – Beispiel-/Vorschaudaten für die lokale Entwicklung (Platzhalter, siehe unten)
- `index.html` – lokale Vorschauseite, bindet den Player per Script-Tag ein

## Lokale Vorschau

```bash
npm install
npm start
```

Anschließend `http://0.0.0.0:8080` im Browser öffnen.

Passe bei Bedarf die Farben in `themes/tankpool24/index.css` unter `:root` an:

```css
:root {
  --main-player-color: #e53533;       /* tankpool24-Rot */
  --main-player-light-color: #fbdad9; /* heller Akzent für den Player-Hintergrund */
  --player-contrast-text: #ffffff;
  --black: #2b2b2b;                   /* Text-/Icon-Farbe */
  --white: #ffffff;
  --grey: #767676;
}
```

**Hinweis:** `podcast.json` enthält aktuell Platzhalter-Metadaten sowie Demo-Mediendateien
von Podigee (nur für die lokale Vorschau, damit der Player im Browser funktioniert).
Sobald der Podcast in Podigee angelegt ist, bitte durch die echten Episoden-/Podcast-Daten
ersetzen (nur relevant für die lokale Vorschau – im Livebetrieb liefert Podigee diese Daten
automatisch).

## Live schalten

1. `themes/tankpool24/index.html` und `themes/tankpool24/index.css` auf einen eigenen,
   CORS-fähigen Webspace hochladen (Header `Access-Control-Allow-Origin: *` oder
   `https://player.podigee-cdn.net`).
2. In den Podcast-Einstellungen bei Podigee unter "Web-Player" → erweiterte Einstellungen
   einblenden → Theme auf "External theme" umstellen und die URLs zu CSS und HTML eintragen.
