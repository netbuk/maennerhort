# Männerhort – Steeldart Altendiez

Flatfile-GitHub-Page (Jekyll, ohne Datenbank) für die Hobbygruppe Steeldart aus Altendiez.

## Aufbau

- `index.md` – Startseite mit den Bereichen Termine (aktuelles Jahr, zweispaltig), Neuigkeiten und Informationen
- `termine-archiv.md` – alle Termine älterer Jahre, nach Jahr gruppiert (verlinkt unter den Terminen)
- `impressum.md` / `datenschutz.md` – Impressum und Datenschutzerklärung (verlinkt im Footer; Platzhalter für Adresse/Kontakt anpassen)
- `_data/termine.yml` – alle Termine (einfach Einträge ergänzen/anpassen)
- `_data/news.yml` – Neuigkeiten
- `_layouts/default.html` – Seitenlayout (Header mit Logo, Navigation, Footer)
- `assets/logo.png` – Gruppenlogo
- `assets/css/style.css` – Gestaltung

## Inhalte bearbeiten

Termine und Neuigkeiten werden als YAML-Dateien in `_data/` gepflegt – es ist keine Datenbank nötig. Änderungen committen und pushen, GitHub Pages baut die Seite automatisch neu.

## GitHub Pages aktivieren

In den Repo-Einstellungen unter **Settings → Pages** als Quelle **GitHub Actions** wählen. Der Workflow `.github/workflows/pages.yml` baut die Seite bei jedem Push auf `main` automatisch mit Jekyll und deployt sie. Die Seite ist danach unter `https://netbuk.github.io/maennerhort/` erreichbar.
