# Copilot Instructions – SBO (Schmalspurbahn-Ordnungswerk)

## Ziel
Du unterstützt beim Schreiben einer technischen Spezifikation („Ordnungswerk") für Schmalspur-Bahnen.
Der Text ist normativ: klar, prüfbar, nicht narrativ.

## Sprachstil (wichtig)
- Schreibe **technisch**, knapp, strukturiert.
- Nutze normative Schlüsselwörter konsequent:
  - **MUST / MUSS** (verpflichtend)
  - **SHOULD / SOLLTE** (empfohlen)
  - **MAY / KANN** (optional)
- Vermeide Storytelling, Anekdoten, Fülltexte.
- **WICHTIG**: Vermeide Begriffe mit rechtlichem oder amtlichem Charakter (z.B. "Verordnung", "Vorschrift", "Regelwerk" für SBO selbst). SBO ist eine private technische Spezifikation ohne gesetzlichen Charakter und ohne Anspruch, eine offizielle Norm zu sein.
- Vermeide autoritative Formulierungen wie "SBO regelt", "vorgeschrieben durch SBO", "SBO fordert". Nutze stattdessen neutrale Formulierungen wie:
  - "Diese Spezifikation definiert..."
  - "Innerhalb dieser Spezifikation..."
  - "Nach dieser Spezifikation..."
  - "Gemäß dieser Spezifikation..."

## Strukturprinzip
- `docs/core/` enthält spurweiten-unabhängige Prinzipien, Definitionen, Methoden.
- `docs/specs/sbo-XXX/` enthält **nur** spurweitenspezifische Parameter und Abweichungen.
- **WICHTIG**: Core-Dateien werden per `include::` in die jeweilige Spurweiten-Spec eingebunden. Der Leser sieht immer nur die fertige SBO-287 (oder SBO-XXX), nicht Core separat. Es gibt keine separate Core-Dokumentation für Endanwender.
- Vermeide Dopplungen:
  - Wenn ein Inhalt in mehreren Specs gilt → in `core/` ablegen und in Specs nur verlinken.
  - Zahlenwerte und Grenzwerte je Spec zentral in `attributes.adoc` pflegen.
- Schreibe Core-Dateien so, dass sie im Kontext der finalen Spurweiten-Spec gelesen werden. Vermeide Formulierungen wie "siehe die Spec-Dokumentation" – der Leser IST bereits in der Spec-Dokumentation.

## Technische Anforderungen an Inhalte
Wenn du Regeln vorschlägst, decke (wo sinnvoll) diese Aspekte ab:
- Lastannahmen: Radlast/Achslast, dynamische Faktoren, Sonderfälle (Stoß, Entgleisung, Punktlast)
- Trassierung: Radien, Achsstände, Überhöhung/Neigung, Übergangsbögen (wenn genutzt)
- Gefälle/Haftung: µ_design, Anfahr-/Bremsnachweise, Nässe/Schmutz als Designfall
- Geschwindigkeit: Streckenklasse, Kurven, Gefälle, Bremsweg, Nutzung (Güter/Personen)
- Fahrzeuge: Achsanordnung, Schwerpunkt, Bremsen, Kupplung, Ladungssicherung
- Gleisbau: Unterbau, Schwellenabstand, Setzungen, Instandhaltung
- Personenverkehr (Klasse P): strengere Limits, Redundanzen, Freigabeprozess
- Prüfung/Wartung: Messgrößen, Toleranzen, Intervalle, Dokumentationspflicht
Orientier dich an der in Deutschland geltenden EBO/BOA, aber passe an Schmalspurbahnen an.

## Formeln & Parameter
- Formeln gehören in `core/` oder Anhang; Parameterwerte in `attributes.adoc`.
- Wenn du Zahlen brauchst, frage nicht nach "Pi mal Daumen",
  sondern lege sie als Parameter mit Begründung/Quelle/Annahme ab.

## Ausgabeformat
- Erzeuge **AsciiDoc** (`.adoc`-Dateien) mit klaren Überschriften und Listen.
- Wenn du Tabellen nutzt: kurze Tabellen, klare Spaltennamen, Einheiten angeben.
- Verwende eindeutige Begriffe (Glossar nutzen/verlinken).
- Nutze AsciiDoc-Syntax für Querverweise, Includes und Attribute.
- Ziel ist ein PDF sowie eine HTML-Dokumentation via GitHub Pagespro Spurweite und Release.

## Versionierung
- Das Projekt folgt **Semantic Versioning** (MAJOR.MINOR.PATCH).
- Alle Änderungen MÜSSEN in der Änderungshistorie-Tabelle im Appendix dokumentiert werden:
  - Core-Änderungen → `docs/core/sbo-core.adoc` Appendix
  - Spec-spezifische Änderungen → Appendix der jeweiligen Spec (z.B. `sbo-287.adoc`)
- Versions-Attribute werden in `attributes.adoc` zentral verwaltet.
- Details zum Release-Prozess siehe `RELEASING.md`.

## Änderungsdisziplin
- Änderungen an Grenzwerten: immer mit kurzer Begründung + betroffene Kapitel referenzieren.
- Änderungen MÜSSEN in der Änderungshistorie-Tabelle im Appendix dokumentiert werden.
- Keine stillen Änderungen quer durch mehrere Dateien: lieber gezielt.
- Bei Breaking Changes (MAJOR): Backwards Compatibility und Migration dokumentieren.
- Versions-Attribute in `attributes.adoc` aktualisieren.

## TODOs
- Format: `// TODO(#<Issue-Nr>): <Kurzbeschreibung>` (AsciiDoc-Zeilenkommentar).
- Jeder TODO-Kommentar verweist auf genau **ein** GitHub Sub-Issue (1:1-Zuordnung).
- Sub-Issues sind wo sinnvoll an Parent-Issues verlinkt (#10–#19).
- Die GitHub Action `alstr/todo-to-issue-action@v5` synchronisiert TODOs automatisch mit Issues.
- Beim Hinzufügen neuer TODOs: erst Sub-Issue anlegen, dann `TODO(#Nr)` im Code setzen.
- Beim Entfernen eines TODOs: Issue wird automatisch geschlossen (CLOSE_ISSUES ist aktiv).
- In der Beschreibung der Issue sollte auch ein Link zu der Stelle im Code enthalten sein, damit die Nachverfolgung einfach ist.

## Sicherheitsleitlinie
- Im Zweifel konservativ auslegen.
- Personenverkehr niemals "nebenbei": immer Klasse P Regeln anwenden.
