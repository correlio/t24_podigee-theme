# tankpool24 – Podigee Themes

Dieses Repository enthält zwei getrennte tankpool24-Themes für zwei unterschiedliche
Podigee-Funktionen. Farben und Formsprache orientieren sich an der tankpool24-Marke
(`#e53533` Rot, dezent abgerundete Ecken, klare Sans-Serif-Typografie) –
siehe [tankpool24.eu](https://www.tankpool24.eu/).

## `files/` – Blog-/Website-Theme (Git-Import)

Das komplette Podigee-Podcast-Website-Layout (Startseite, Episodenseite, Archiv,
Über-uns-Seite, Sidebar, Kommentare, Transkript). Wird über **"Repository URL (git)"**
in den Podigee-Theme-Einstellungen importiert.

**Wichtig:** Podigee erwartet dafür zwingend einen Ordner namens `files/` im
Root-Verzeichnis des Repos – nur `.html`- und `.css`-Dateien darin werden importiert
(max. 50 Dateien). Beim Import die **HTTPS**-Repo-URL verwenden:

```
https://github.com/correlio/t24_podigee-theme.git
```

Mehr Details: [Podigee-Hilfe: Importing Themes from Git Repos](https://help.podigee.com/article/160-importing-themes-from-git-repos).

Struktur:

- `files/layout.html` – Grundgerüst (Header, Navigation, Sidebar-Einbindung)
- `files/index.html` – Episodenliste (Startseite)
- `files/show.html` – einzelne Episodenseite
- `files/archive.html` – Episodenarchiv
- `files/about.html` – Über-uns-Seite
- `files/sidebar.html` – Sidebar (Beschreibung, Abo-Links, Social Links)
- `files/navigation.html` – Hauptnavigation
- `files/comments.html` – Kommentarbereich
- `files/transcript.html` – Transkript-Seite
- `files/application.css` – Styling mit tankpool24-Farben (Variablen in `:root`)

Nach einem erneuten Import werden alle vorhandenen Theme-Dateien in Podigee gelöscht
und durch den aktuellen Stand des Repos ersetzt.

## `webplayer/` – Custom Webplayer-Theme (manuelle URL-Konfiguration)

Das eingebettete Audio-Player-Widget, gebaut auf Basis des
[podigee-podcast-player-theme-sdk](https://github.com/podigee/podigee-podcast-player-theme-sdk).
Dieses Theme wird **nicht** per Git importiert, sondern die beiden Datei-URLs (CSS + HTML)
werden manuell eingetragen.

### Lokale Vorschau

```bash
cd webplayer
npm install
npm start
```

Anschließend `http://localhost:8080` im Browser öffnen.

Farben lassen sich in `webplayer/theme/index.css` unter `:root` anpassen:

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

**Hinweis:** `webplayer/podcast.json` enthält Platzhalter-Metadaten sowie Demo-Mediendateien
von Podigee (nur für die lokale Vorschau, damit der Player im Browser funktioniert) –
im Livebetrieb liefert Podigee diese Daten automatisch.

### Live schalten

1. `webplayer/theme/index.html` und `webplayer/theme/index.css` auf einen eigenen,
   CORS-fähigen Webspace hochladen (Header `Access-Control-Allow-Origin: *` oder
   `https://player.podigee-cdn.net`).
2. In den Podcast-Einstellungen bei Podigee unter "Web-Player" → erweiterte Einstellungen
   einblenden → Theme auf "External theme" umstellen und die URLs zu CSS und HTML eintragen.
