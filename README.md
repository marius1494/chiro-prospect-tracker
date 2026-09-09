# Chiro Prospect Tracker

Kleiner statischer Tracker für die US-Chiropraktiker-Akquise (YouTube-Agentur).
Kein Build, keine Abhängigkeiten. Eine HTML-Datei + eine JSON-Datei.

## Dateien

- `index.html` — die Oberfläche (Tabelle, Filter, inline bearbeiten, GitHub-Auto-Sync). Self-contained.
- `data.json` — **die einzige Datenquelle.** Ein Objekt = ein Prospect. Von Hand editierbar.

## Ansehen

- **GitHub Pages:** `https://marius1494.github.io/chiro-prospect-tracker/`
- **Lokal:** im Ordner `python3 -m http.server` starten, dann `http://localhost:8000/` öffnen.
  (Doppelklick auf `index.html` funktioniert nicht — der Browser blockiert dann das Laden von `data.json`.)

## Bearbeiten — zwei Wege

**A) In der Oberfläche.** Alle Felder direkt in der Tabellenzeile bearbeiten (kein Aufklappen mehr).
Link-Spalten (YouTube, Web/IG) über das ✎ setzen. Mit hinterlegtem GitHub-Token (Button **⇅ Sync**)
wird jede Änderung nach ~1,5&nbsp;s automatisch nach GitHub gespeichert; ohne Token nur lokal / nur lesen.

**B) Direkt in `data.json`.** Datei im Editor öffnen, Objekt ändern/hinzufügen, committen, pushen.

`status`-Werte: `Neu` · `Angeschrieben` · `Follow-up 1` · `Follow-up 2` · `Antwort erhalten` ·
`Call vereinbart` · `Kunde` · `Kein Fit` · `Abgesagt`

## Zusammenarbeit (2 Personen + jeweils Claude)

Git ist das Sync-Werkzeug. Vor dem Bearbeiten `git pull`, danach `git commit` + `git push`.
Bei Parallelbearbeitung kann es einen Merge-Konflikt in `data.json` geben — der lässt sich
zeilenweise auflösen (ein Prospect pro Block). Claude (beide Rechner) kann `data.json` direkt
bearbeiten und committen.

## Spalten (Oberfläche)

Name · Stadt · YouTube · Web / IG · Bearbeiter · Status · E-Mail · Angeschrieben (Datum) ·
FU 1 / FU 2 (Häkchen + Datum) · Löschen (✕).

`data.json` kann darüber hinaus weitere Felder pro Prospect enthalten (z. B. `score`, `moneySignal`,
`notes`, `subs`, `lastUpload`, `bestVideoViews`, `source`, `hookVideoTitle`) — die werden aktuell
nicht in der Tabelle angezeigt, bleiben beim Speichern aber erhalten.
