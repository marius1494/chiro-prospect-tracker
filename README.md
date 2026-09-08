# Chiro Prospect Tracker

Kleiner statischer Tracker für die US-Chiropraktiker-Akquise (YouTube-Agentur).
Kein Build, keine Abhängigkeiten. Eine HTML-Datei + eine JSON-Datei.

## Dateien

- `index.html` — die Oberfläche (Tabelle, Filter, Bearbeiten, Export). Self-contained.
- `data.json` — **die einzige Datenquelle.** Ein Objekt = ein Prospect. Von Hand editierbar.

## Ansehen

- **GitHub Pages:** nach Aktivierung unter `https://<user>.github.io/<repo>/`
- **Lokal:** im Ordner `python3 -m http.server` starten, dann `http://localhost:8000/` öffnen.
  (Doppelklick auf `index.html` funktioniert nicht — der Browser blockiert dann das Laden von `data.json`.)

## Bearbeiten — zwei Wege

**A) In der Oberfläche.** Zeile anklicken → Felder bearbeiten. Änderungen liegen zunächst nur im
Browser (localStorage). Zum dauerhaften Speichern: Button **Exportieren → „data.json herunterladen"**,
die Datei im Repo ersetzen, committen, pushen.

**B) Direkt in `data.json`.** Datei im Editor öffnen, Objekt ändern/hinzufügen, committen, pushen.

`status`-Werte: `Neu` · `Angeschrieben` · `Follow-up 1` · `Follow-up 2` · `Antwort erhalten` ·
`Call vereinbart` · `Kunde` · `Kein Fit` · `Abgesagt`
`score`: 1–3 (3 = bester Fit). `nextActionDate` im Format `YYYY-MM-DD` (wird rot, wenn fällig/überfällig).

## Zusammenarbeit (2 Personen + jeweils Claude)

Git ist das Sync-Werkzeug. Vor dem Bearbeiten `git pull`, danach `git commit` + `git push`.
Bei Parallelbearbeitung kann es einen Merge-Konflikt in `data.json` geben — der lässt sich
zeilenweise auflösen (ein Prospect pro Block). Claude (beide Rechner) kann `data.json` direkt
bearbeiten und committen.

## Spalten

Pipeline-Basis (wie im alten Google Sheet): Name, YouTube, Website, Instagram, E-Mail,
Angeschrieben, Follow-up, Zusage/Status, Bearbeiter.
Ergänzt: Stadt/State, Score, Abos, Letzter Upload, Bestes Video (Views), Money-Signal,
Video-Titel für den Personalisierungs-Hook, Follow-up-1/2-Datum, Nächste Aktion (+ Datum), Notizen, Quelle.
