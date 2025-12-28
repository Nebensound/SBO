# SBO – Smallspurbahn-Ordnungswerk

**Technische Spezifikation für Planung, Bau und Betrieb von Schmalspur-Bahnen**

## Was ist SBO?

SBO ist ein privates, offenes Engineering-Ordnungswerk für Schmalspur-Bahnen (Garten- und Parkbahnen). Es definiert:

* **Klassensysteme** für Last, Geschwindigkeit und Betriebsart
* **Technische Anforderungen** an Gleisbau, Fahrzeuge und Betrieb
* **Berechnungsmethoden** für Lastannahmen, Trassierung und Bremsen
* **Sicherheitsrichtlinien** für Güter- und Personenverkehr

Das Ordnungswerk ist modular aufgebaut: Jede Spurweite hat ihre eigene Spezifikation mit konkreten Grenzwerten (z. B. SBO-287 für 287 mm Spurweite).

## 📖 Dokumentation

Die vollständige, aktuelle Dokumentation finden Sie hier:

### **→ [nebensound.github.io/SBO](https://nebensound.github.io/SBO/)**

Dort sind alle verfügbaren Spezifikationen aufgeführt.

## 📦 Downloads

PDF-Versionen der Spezifikationen können Sie bei den [Releases](../../releases) herunterladen.

## 📋 Versionierung

Das Projekt folgt [Semantic Versioning](https://semver.org/lang/de/). Änderungen werden in den Appendices der jeweiligen Dokumente dokumentiert:

* **Core-Änderungen**: [sbo-core.adoc](docs/core/sbo-core.adoc) Appendix
* **Spec-Änderungen**: Appendix der jeweiligen Spurweiten-Spec (z.B. [sbo-287.adoc](docs/specs/sbo-287/sbo-287.adoc))

Für Informationen zum Release-Prozess siehe [RELEASING.md](RELEASING.md).

## 🏗️ Für Entwickler

Dieses Repository enthält die AsciiDoc-Quelldateien. Die Struktur:

```
docs/
├── core/           # Inhaltliche Kapitel (ohne Zahlenwerte)
└── specs/          # Spurweitenspezifische Parameter
    ├── sbo-287/    # 287 mm Spurweite
    └── ...         # Weitere Spurweiten
```

### Lokal bauen

```bash
# HTML Preview
asciidoctor docs/specs/sbo-287/sbo-287.adoc

# PDF
asciidoctor-pdf docs/specs/sbo-287/sbo-287.adoc -o sbo-287.pdf
```

### GitHub Actions

* **Push/PR:** Testet Build-Fähigkeit
* **Release:** Baut PDFs und publiziert auf GitHub Pages

## ⚖️ Rechtliches

Privates Ordnungswerk ohne rechtliche Bindung. Nutzung auf eigenes Risiko. Keine Gewährleistung, keine Haftung.

