# Werkbank einrichten

Richtet eine neue Werkbank-Arbeitsumgebung im aktuellen Verzeichnis ein.

## Trigger

- "Werkbank einrichten"
- "Setup"
- "Werkbank aufsetzen"

## Template-Quellen (relativ zum Plugin-Verzeichnis)

```
templates/
├── KONTEXT.md.template           → wird zu KONTEXT.md (Platzhalter ersetzen)
├── regeln/
│   ├── regelsystem.md            → Werkbank/Regeln/regelsystem.md (1:1 kopieren)
│   └── projektstruktur.md        → Werkbank/Regeln/projektstruktur.md (1:1 kopieren)
├── MANIFEST-projekt.md           → Werkbank/Vorlagen/MANIFEST-projekt.md (1:1 kopieren)
├── MANIFEST-engagement.md        → Werkbank/Vorlagen/MANIFEST-engagement.md (1:1 kopieren)
├── PROFIL.md                     → Werkbank/Vorlagen/PROFIL.md (1:1 kopieren)

rollen/
├── Manager/SYSTEM.md             → Werkbank/Rollen/Manager/SYSTEM.md (wenn gewaehlt)
└── TechLead/SYSTEM.md            → Werkbank/Rollen/TechLead/SYSTEM.md (wenn gewaehlt)
```

Lies die Template-Dateien mit dem Read-Tool aus dem Plugin-Verzeichnis und schreibe sie
an die Zielorte im Arbeitsverzeichnis des Nutzers.

## Ablauf

### Schritt 1: Nutzer befragen

Stelle diese Fragen (alle auf einmal, nicht einzeln):

1. **Wer bist du?** Name, Unternehmen/Marke, eine Mission in einem Satz.
2. **Was machst du?** Kernaktivitaet in 2-3 Saetzen.
3. **Welche Rollen brauchst du?** Zeige die verfuegbaren Referenz-Rollen:
   - **Manager** — Verarbeitet Transkripte, pflegt Engagements, verwaltet Personen-Profile
   - **Tech-Lead** — Technische Architektur, Code-Entscheidungen, Arbeitspaket-Spezifikation
   - Hinweis: "Du kannst spaeter eigene Rollen anlegen. Diese zwei sind Startpunkte."

### Schritt 2: Verzeichnisstruktur anlegen

```
[Arbeitsverzeichnis]/
├── KONTEXT.md
├── Werkbank/
│   ├── Regeln/
│   │   ├── regelsystem.md
│   │   └── projektstruktur.md
│   ├── Rollen/
│   │   ├── Manager/SYSTEM.md      (wenn gewaehlt)
│   │   └── TechLead/SYSTEM.md     (wenn gewaehlt)
│   └── Vorlagen/
│       ├── MANIFEST-projekt.md
│       ├── MANIFEST-engagement.md
│       └── PROFIL.md
├── Projekte/
├── Engagements/
│   ├── Aktiv/
│   └── Archiv/
└── Wissen/
    ├── Thesen/
    ├── Konzepte/
    ├── Recherche/
    └── Stimmen/
```

### Schritt 3: KONTEXT.md befuellen

Nutze das Template aus `templates/KONTEXT.md.template`.
Ersetze alle Platzhalter mit den Angaben aus Schritt 1.
Befuelle die Regeltabelle mit vollstaendigen Triggern (aus den kopierten Regeldateien).
Befuelle die Rollentabelle mit vollstaendigen Triggern (aus den kopierten SYSTEM.md-Dateien —
jede Rolle hat eine ## Trigger Sektion, aus der die Trigger extrahiert werden).

WICHTIG: Die Trigger-Spalten muessen ALLE Trigger enthalten — vollstaendig,
nicht auszugsweise. Jedes Schluesselwort in Anfuehrungszeichen, jede
Kontext-Bedingung mit "oder Kontext: ...".

### Schritt 4: Hinweis an den Nutzer

Sage dem Nutzer:

> Deine Werkbank ist eingerichtet. Damit Claude sie automatisch laedt,
> trage diesen Satz in deine globalen CoWork-Einstellungen (Custom Instructions) ein:
>
> **"Wenn eine Datei namens KONTEXT.md im Root des Arbeitsverzeichnisses liegt, lies sie zuerst."**
>
> Du kannst jetzt:
> - "Projekt anlegen" sagen, um ein neues Projekt zu starten
> - "Engagement anlegen" sagen, um ein neues Klientenmandat zu starten
> - "Rolle anlegen" sagen, um eine eigene Rolle zu erstellen
> - "Regel erstellen" sagen, um neue Regeln festzuhalten
