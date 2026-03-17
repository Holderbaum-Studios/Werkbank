<!-- werkbank-template: regelsystem v2.0 -->
# Regelsystem

Meta-Regel: Beschreibt wo Regeln liegen, welches Format sie haben, und wie neue Regeln erstellt oder aktualisiert werden. Diese Regel wird bei Session-Start geladen.

```regel
name: regelsystem
beschreibung: Bootstrap-Regel fuer das Werkbank-Regelsystem

trigger:
  - "Regel erstellen", "Regel aendern", "mach eine Regel draus"
  - "Lernen festhalten", "das soll nie wieder passieren"
  - "Rolle anlegen", "neue Rolle", "Rolle erstellen"
  - Kontext: Wenn nach einer Korrektur darum gebeten wird,
    ein Verhalten dauerhaft festzuhalten
  - Kontext: Wenn eine neue Rolle in Werkbank/Rollen/ angelegt
    oder eine bestehende Rolle veraendert wird

aktionen:
  - vorschlagen: |
      Regeln leben in: Werkbank/Regeln/
      Format: Markdown mit ```regel-Block
      Dateiname: kebab-case.md (deutsch, keine Umlaute)

      Jede Regel-Datei hat diese Struktur:

      1. Ueberschrift (# Regelname)
      2. Kurzbeschreibung (ein Satz)
      3. ```regel-Block mit:
         - name: kebab-case-identifier
         - beschreibung: Was die Regel tut
         - trigger: Wann sie greift (Schluesselwoerter + Kontextbeschreibung)
         - aktionen: Was passiert (ablehnen / vorschlagen / ausfuehren)
         - beispiele: Mindestens ein eingabe/ausgabe-Paar
         - metadaten: prioritaet + version

      Aktions-Typen:
      - ablehnen: "Tu das NICHT" + Begruendung
      - vorschlagen: "Tu stattdessen DAS"
      - ausfuehren: Konkreten Befehl/Workflow ausfuehren

      Prioritaeten: kritisch > hoch > mittel > niedrig

  - ausfuehren: |
      Nach dem Erstellen oder Aendern einer Regel:
      1. Regeldatei in Werkbank/Regeln/ schreiben
      2. Regel-Index in KONTEXT.md aktualisieren (Tabelle unter "## Regelsystem")
         WICHTIG: Die Trigger-Spalte muss ALLE Trigger enthalten — vollstaendig,
         nicht auszugsweise. Das heisst:
         - Jedes Schluesselwort in Anfuehrungszeichen auflisten
         - Jede Kontext-Bedingung mit "oder Kontext: ..." anfuegen
         - Keine Kurzformen, keine Auslassungen
         Format-Beispiel:
         | Regelname | "Trigger A", "Trigger B", oder Kontext: Beschreibung | `Werkbank/Regeln/datei.md` |
      Beide Schritte sind Pflicht. Ohne KONTEXT-Update ist die Regel nicht fertig.

      Rollen-Anlage und -Aenderung:
      Rollen leben in: Werkbank/Rollen/[Rollenname]/SYSTEM.md
      Nach dem Erstellen oder Aendern einer Rolle:
      1. SYSTEM.md in Werkbank/Rollen/[Rollenname]/ schreiben
      2. Rollen-Index in KONTEXT.md aktualisieren (Tabelle unter "## Rollen")
         WICHTIG: Die Trigger-Spalte muss ALLE Trigger enthalten — vollstaendig,
         nicht auszugsweise. Gleiche Regeln wie bei Regel-Triggern:
         - Jedes Schluesselwort in Anfuehrungszeichen auflisten
         - Jede Kontext-Bedingung mit "oder Kontext: ..." anfuegen
         - Keine Kurzformen, keine Auslassungen
         Format-Beispiel:
         | Rollenname | "Trigger A", "Trigger B", oder Kontext: Beschreibung | `Werkbank/Rollen/Name/SYSTEM.md` |
      Beide Schritte sind Pflicht. Ohne KONTEXT-Update ist die Rolle nicht fertig.

beispiele:
  - eingabe: "Der Agent empfiehlt immer Bullet-Points in Fliesstext"
    ausgabe: |
      Neue Datei: Werkbank/Regeln/keine-bullets-in-fliesstext.md
      Trigger: "Text erstellen", "Fliesstext"
      Aktion: ablehnen + vorschlagen (Aufzaehlung in natuerlicher Sprache)
      Index-Eintrag in KONTEXT.md ergaenzen (mit vollstaendigen Triggern)

  - eingabe: "Leg mir eine neue Rolle an: Researcher"
    ausgabe: |
      Neues Verzeichnis: Werkbank/Rollen/Researcher/
      Neue Datei: Werkbank/Rollen/Researcher/SYSTEM.md
      Trigger aus SYSTEM.md extrahieren (alle Schluesselwoerter + Kontexte)
      Rollen-Tabelle in KONTEXT.md ergaenzen mit vollstaendigen Triggern

metadaten:
  prioritaet: kritisch
  version: 2.0
```
