# Copilot Instructions – SBO (Smallspurbahn-Ordnungswerk)

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

## Strukturprinzip
- `docs/core/` enthält spurweiten-unabhängige Prinzipien, Definitionen, Methoden.
- `docs/specs/sbo-XXX/` enthält **nur** spurweitenspezifische Parameter und Abweichungen.
- Vermeide Dopplungen:
  - Wenn ein Inhalt in mehreren Specs gilt → in `core/` ablegen und in Specs nur verlinken.
  - Zahlenwerte und Grenzwerte je Spec zentral in `00_parameter.md` pflegen.
- es soll eine Dokumentation je Spurweite entstehen, jedoch keine eigene für Core. Core solle aber den gesamten Überbau und Kontext liefern.

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
Orientier dich an der in Deutschland geltenden EBO/BOA, aber passe an Smallspurbahnen an.

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

## Sicherheitsleitlinie
- Im Zweifel konservativ auslegen.
- Personenverkehr niemals "nebenbei": immer Klasse P Regeln anwenden.
