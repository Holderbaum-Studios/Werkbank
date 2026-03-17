# Werkbank

Eine strukturierte Arbeitsumgebung fuer [Claude CoWork](https://claude.ai) — mit Rollen, Regeln und Vorlagen.

## Was ist das?

Die Werkbank gibt dir eine Verzeichnisstruktur und Konventionen, die ein KI-Agent versteht und befolgt. Du bekommst:

- **Rollen** — Spezialisierte Agenten mit eigenem Verhalten (z.B. Manager, Tech-Lead)
- **Regeln** — Verhaltensregeln, die Claude automatisch befolgt (z.B. Projektstruktur, Dateikonventionen)
- **Vorlagen** — Templates fuer Projekte, Engagements, Manifeste

Alles wird ueber eine zentrale `KONTEXT.md` gesteuert, die Claude beim Start liest.

## Installation

In Claude CoWork unter Settings → Plugins diesen Marketplace hinzufuegen:

```
Holderbaum-Studios/Werkbank
```

## Quick Start

Nach der Installation:

1. Oeffne einen leeren Ordner in CoWork (das wird dein Arbeitsverzeichnis)
2. Sage: **"Werkbank einrichten"**
3. Beantworte die Setup-Fragen (Wer bist du, was machst du, welche Rollen)
4. Trage in deine globalen CoWork Custom Instructions ein:
   *"Wenn eine Datei namens KONTEXT.md im Root des Arbeitsverzeichnisses liegt, lies sie zuerst."*
5. Fertig — deine Werkbank ist einsatzbereit

## Was du bekommst

```
Dein-Arbeitsverzeichnis/
├── KONTEXT.md              Zentrale Steuerungsdatei (Claude liest sie zuerst)
├── Werkbank/
│   ├── Regeln/             Verhaltensregeln fuer Agenten
│   ├── Rollen/             Spezialisierte Agenten-Persoenlichkeiten
│   └── Vorlagen/           Templates fuer Projekte und Engagements
├── Projekte/               Alles woran gearbeitet wird
├── Engagements/            Zeitgebundene Klientenarbeit
└── Wissen/                 Thesen, Konzepte, Recherche, Stimmen
```

## Mitgelieferte Rollen

| Rolle | Beschreibung |
|-------|-------------|
| Manager | Verarbeitet Transkripte, pflegt Engagements, verwaltet Personen-Profile |
| Tech-Lead | Technische Architektur, Code-Entscheidungen, Arbeitspaket-Spezifikation |

Du kannst jederzeit eigene Rollen anlegen. Sage einfach: "Rolle anlegen".

## Eigene Rollen und Regeln

Die Werkbank ist ein Startpunkt, kein Kaefig. Du kannst:

- **Eigene Rollen erstellen:** "Leg mir eine neue Rolle an: [Name]"
- **Eigene Regeln definieren:** "Mach eine Regel draus" (nach einer Korrektur)
- **Vorlagen anpassen:** Alles in `Werkbank/Vorlagen/` gehoert dir

## Updates

```
# Sage in CoWork:
"Werkbank aktualisieren"
```

Der Update-Skill prueft, ob neue Versionen von Regeln oder Vorlagen verfuegbar sind, zeigt dir die Aenderungen, und pflegt sie ein — ohne deine Anpassungen zu ueberschreiben.

## Repo-Struktur

```
.claude-plugin/
└── marketplace.json                Marketplace-Manifest
werkbank/                           Das Plugin
├── .claude-plugin/plugin.json      Plugin-Manifest
├── skills/
│   ├── setup/SKILL.md              "Werkbank einrichten"
│   └── update/SKILL.md             "Werkbank aktualisieren"
├── templates/                      Was beim Setup kopiert wird
│   ├── KONTEXT.md.template
│   ├── regeln/                     Bootstrap-Regeln
│   ├── MANIFEST-projekt.md
│   ├── MANIFEST-engagement.md
│   └── PROFIL.md
└── rollen/                         Referenz-Rollen
    ├── Manager/SYSTEM.md
    └── TechLead/SYSTEM.md
LICENSE
README.md
```

## Lizenz

MIT — siehe [LICENSE](LICENSE)
