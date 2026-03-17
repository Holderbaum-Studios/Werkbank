<!-- werkbank-template: projektstruktur v1.2 -->
# Projektstruktur

Beschreibt den Aufbau von Projekten und das Arbeitspaket-Management.

```regel
name: projektstruktur
beschreibung: Aufbau von Projektverzeichnissen und Arbeitspaket-Lifecycle

trigger:
  - "Projekt anlegen", "Arbeitspaket anlegen", "Arbeitspaket spezifizieren"
  - "In einem Projekt arbeiten", "Projektstruktur"
  - Kontext: Immer wenn ein Agent in einem Projektverzeichnis arbeitet
    oder ein neues Projekt aufsetzen soll

aktionen:
  - vorschlagen: |
      Projekte werden in klar definierten Arbeitspaketen organisiert —
      gross genug, um sinnvoll zu sein, klein genug, um abschliessbar zu bleiben.

      Aufbau:

      Projekte/[Name]/
      ├── MANIFEST.md           Vision, Ziele, aktueller Stand, Ideen-Sammlung
      ├── Arbeitspakete/        Nummerierte Pakete
      │   ├── 001-[name].md     Status: offen / in-arbeit / erledigt
      │   ├── 002-[name].md
      │   └── ...
      ├── Verlauf/              Sitzungen/Calls: YYYY-MM-DD-[titel]/
      ├── Ideen/                Optional: komplexere Ideen als eigene Dateien
      └── App/                  Optional: Code-Verzeichnis

      MANIFEST.md enthaelt:
      - Vision und Produktphilosophie
      - Aktueller Stand (was in Arbeit, was als naechstes)
      - Ideen-Sammlung: ungeformte Gedanken, die noch kein Arbeitspaket sind

      Ideen-Sammlung in der MANIFEST.md:
      - Einfache Ideen stehen direkt als Liste in der MANIFEST.md
      - Komplexere Ideen bekommen eine Datei in Ideen/ und werden verlinkt
      - Wenn eine Idee konkret genug wird: Nummer vergeben, nach Arbeitspakete/ verschieben

      Arbeitspaket-Lifecycle:
      Idee → offen (Arbeitspaket-Datei mit Nummer) → in-arbeit → erledigt

      Arbeitspakete sind monoton nummeriert (001, 002, 003...) fuer
      chronologische Uebersicht. Der Status steht im YAML-Header:

      ---
      status: offen | in-arbeit | erledigt
      ---

beispiele:
  - eingabe: "Neues Projekt anlegen"
    ausgabe: |
      mkdir Projekte/[Name]
      MANIFEST.md anlegen mit Vision und erster Ideen-Sammlung
      KONTEXT.md Projekttabelle aktualisieren

  - eingabe: "Die Idee soll jetzt ein Arbeitspaket werden"
    ausgabe: |
      Naechste freie Nummer ermitteln (z.B. 005)
      Arbeitspakete/005-[name].md erstellen
      YAML-Header: status: offen
      Idee aus MANIFEST.md entfernen oder als "→ Paket 005" markieren

metadaten:
  prioritaet: hoch
  version: 1.2
```
