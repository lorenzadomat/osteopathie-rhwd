# Praxis für Osteopathie Gesa Adomat — Website

Statische Website, ein Ordner je Entwurf. Kein Build-Schritt, kein npm nötig:
Die HTML-Dateien lassen sich direkt hochladen.

## Entwürfe ansehen

`index.html` im Projektordner öffnen — sie verlinkt alle drei Entwürfe.
Sie ist nur zur Abstimmung da und gehört **nicht** zur fertigen Seite.

| Ordner | Entwurf | Charakter |
|---|---|---|
| `design-1-linie/` | **Linie** | Ruhig, editorial. Sandton, Fraunces-Serife. Ein durchgehender Faden wird beim Scrollen gezeichnet und verbindet alle Abschnitte. |
| `design-2-kartei/` | **Kartei** | Klar, strukturiert. Weiß mit vollflächigen Farbbändern, Manrope-Grotesk. Dauer und Preise stehen im auffälligsten Element der Seite. |
| `design-3-handauflegen/` | **Handauflegen** | Warm, markant. Tiefrot als tragende Fläche, Epilogue in Großformat, das Gestaltungselement überformatig angeschnitten. Auf dem Handy eine feste Anrufleiste. |

Jeder Ordner enthält `index.html`, `impressum.html` und `style.css`.

## Gemeinsame Dateien

```
assets/fonts/   selbst gehostete Schriften (woff2)
assets/img/     logo.svg, element.svg, favicon.svg, _sprite.html
```

Alle drei Entwürfe greifen über `../assets/…` darauf zu. Sobald ein Entwurf
feststeht, wird sein Ordner mitsamt `assets/` zur eigentlichen Website —
dabei die Pfade von `../assets/` auf `assets/` anpassen.

Die Schriften liegen **lokal** im Projekt und werden nicht von Google geladen.
Das ist in Deutschland die datenschutzrechtlich saubere Variante; bitte so lassen.

## Skripte

| Befehl | Zweck |
|---|---|
| `python3 daten.py` | Setzt Praxisdaten (Adresse, Telefon, E-Mail, Sprechzeiten) in alle Seiten ein. Werte oben in der Datei anpassen, dann ausführen. Am Ende werden noch offene Platzhalter aufgelistet. |
| `python3 build.py` | Fügt das SVG-Sprite ein und ergänzt fehlende `viewBox`-Angaben. Nach Änderungen am Markup ausführen. |
| `python3 assets/img/_erzeuge-assets.py` | Erzeugt Logo, Gestaltungselement, Favicon und Sprite neu aus den Originalen in `images/`. Nur nötig, wenn sich die Originaldateien ändern. |

Zum lokalen Ansehen mit korrekten Pfaden:
`python3 -m http.server 8000` und dann <http://localhost:8000> öffnen.

## Was noch fehlt

### Offene Platzhalter
Im Impressum sind noch Angaben offen — sie sind im Quelltext als `[[…]]`
markiert und auf der Seite farbig hinterlegt:

- zuständiges Gesundheitsamt (für Rheda-Wiedenbrück der Kreis Gütersloh — Anschrift bitte prüfen)
- Berufsverband und Mitgliedsnummer
- Berufshaftpflichtversicherung: Name, Anschrift, räumlicher Geltungsbereich
- USt-IdNr., falls vorhanden
- Bildnachweis: Urheber von Logo/Gestaltung und Fotograf:in

`daten.py` listet nach jedem Lauf auf, was noch offen ist.

### Fotos
Entwurf 2 hat ein markiertes Platzhalterfeld im Hochformat 4:5 für ein Porträt
oder ein Praxisfoto. Sobald ein Bild vorliegt, ersetzt es den Platzhalter.
Entwurf 1 und 3 kommen ohne Foto aus, vertragen aber eines.

### Datenschutzerklärung
Bewusst **nicht** angelegt, weil nur Impressum beauftragt war. Eine
Datenschutzerklärung ist für eine deutsche Website aber auch ohne
Kontaktformular erforderlich (Server-Logs des Hosters). Sage Bescheid,
wenn ich eine ergänzen soll — es wäre eine weitere Unterseite plus ein
Link in der Fußzeile.

## Texte

Aus `.docs/website-content.txt` übernommen: Berufsbezeichnungen, Dauer und
Preise, der Hinweis zum Anrufbeantworter, der Verweis auf den VOD sowie die
Angaben zur Kostenerstattung (für den FAQ-Bereich in vier Fragen gegliedert).

Von mir formuliert und daher **bitte fachlich gegenlesen**:

- der Abschnitt „Was Osteopathie ist" (zwei Absätze)
- die drei Prinzipien (Einheit / Struktur und Funktion / Selbstregulation)
- die Überschriften und die Einleitungssätze im Hero

Die Texte sind bewusst beschreibend gehalten und enthalten keine
Wirkversprechen — das Heilmittelwerbegesetz setzt hier enge Grenzen.

## Technische Basis

- Reines HTML, CSS und wenig JavaScript. Keine Abhängigkeiten, kein Build.
- Responsiv ab 320 px Breite.
- Tastaturbedienbar, sichtbarer Fokusrahmen, Sprunglink zum Inhalt.
- `prefers-reduced-motion` wird respektiert: Animationen entfallen dann.
- Farben laut Vorgabe: `#e1ddda`, `#c9c4be`, `#c93947`, `#942e32`.
