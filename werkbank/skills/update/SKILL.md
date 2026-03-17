# Werkbank aktualisieren

Prueft ob neue Versionen von Regeln oder Vorlagen verfuegbar sind und pflegt Aenderungen ein — ohne Nutzerdaten zu ueberschreiben.

## Trigger

- "Werkbank aktualisieren"
- "Werkbank updaten"
- "Gibt es Updates?"

## Versionierung

Jedes Template hat einen Versions-Header in der ersten Zeile:
```
<!-- werkbank-template: [name] v[X.Y] -->
```

Der Skill vergleicht die installierte Version (im Arbeitsverzeichnis) mit der aktuellen Version (im Plugin unter `templates/`).

## Ablauf

### Schritt 1: Versionen pruefen

Lies alle Dateien im Arbeitsverzeichnis, die einen `werkbank-template`-Header haben:
- `Werkbank/Regeln/regelsystem.md`
- `Werkbank/Regeln/projektstruktur.md`

Lies die entsprechenden Dateien aus dem Plugin-Verzeichnis unter `templates/`.

Vergleiche die Versionen.

### Schritt 2: Bericht erstellen

Zeige dem Nutzer eine Uebersicht:

```
Werkbank-Update-Check:

Regeln:
  regelsystem.md      — installiert: v1.0, verfuegbar: v2.0 ⚡ Update
  projektstruktur.md  — installiert: v1.0, verfuegbar: v1.1 ⚡ Update

Neue Dateien:
  [name].md           — Neue Regel, noch nicht installiert

Rollen:
  Manager/SYSTEM.md   — nicht versioniert (nutzereigen, kein Update)
```

### Schritt 3: Updates vorschlagen

Fuer jede Datei mit verfuegbarem Update:

1. Zeige die Aenderungen zwischen alter und neuer Template-Version (kurze Zusammenfassung, kein voller Diff)
2. Frage: "Soll ich das einpflegen?"
3. Bei Ja:
   - Wenn der Nutzer die Datei NICHT veraendert hat (identisch mit dem alten Template): Datei ersetzen
   - Wenn der Nutzer die Datei veraendert hat: Die neuen Aenderungen des Templates manuell in die existierende Datei einarbeiten (Merge), ohne Nutzer-Anpassungen zu ueberschreiben
   - Versions-Header aktualisieren
4. KONTEXT.md Tabellen aktualisieren, falls sich Trigger geaendert haben

### Schritt 4: Neue Dateien vorschlagen

Fuer Dateien, die im Plugin existieren aber nicht im Arbeitsverzeichnis:

1. Beschreibe kurz, was die neue Datei tut
2. Frage: "Soll ich sie installieren?"
3. Bei Ja: Datei kopieren + KONTEXT.md Index aktualisieren (mit vollstaendigen Triggern)

## Wichtig

- **Niemals** Nutzerdateien blind ueberschreiben
- **Niemals** Rollen-SYSTEM.md automatisch updaten — Rollen gehoeren dem Nutzer, auch wenn sie urspruenglich aus dem Plugin kamen
- **Immer** die KONTEXT.md Tabellen synchron halten
