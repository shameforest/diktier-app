# Diktier-App

Offline-Diktier-App für Windows: Tastenkürzel drücken, sprechen – der Text erscheint in der App, in der du gerade schreibst (E-Mail, WhatsApp Desktop, Word, Browser, beliebige Textfelder).

- **Komplett offline:** Die Spracherkennung läuft lokal. Kein Audio verlässt den Rechner.
- **Keine KI-Nachbearbeitung:** Satzzeichen und Großschreibung kommen nur vom Erkennungsmodell selbst oder von festen, nachvollziehbaren Regeln – nie von einem Sprachmodell (LLM).
- **Deutsch und Englisch**, auch gemischt.

> Status: in Entwicklung (Stufe 0 – Fork & Build). Die Oberfläche ist bis zur Design-Stufe noch die von Handy.

## Herkunft und Lizenzen

- Dieses Projekt ist ein eigenständiger Fork von **[Handy](https://github.com/cjpais/Handy)** von CJ Pais, veröffentlicht unter der MIT-Lizenz (siehe [LICENSE](LICENSE)). Vielen Dank an alle Handy-Mitwirkenden.
- Gegenüber Handy entfernt: LLM-Nachbearbeitung (OpenAI, Anthropic, Groq, OpenRouter, Apple Intelligence u. a.) samt API-Schlüsseln und Prompts, der Auto-Updater, die Code-Signierung über Handys Konto sowie alle macOS-/Linux-Workflows.
- Spracherkennungsmodelle haben eigene Lizenzen, z. B. **NVIDIA Parakeet TDT 0.6B v3** (CC-BY-4.0) und **OpenAI Whisper** (MIT).

## Bauen unter Windows

Voraussetzungen: Rust (stable, MSVC), Bun, MSVC-Compiler + Windows SDK, CMake, Ninja, Vulkan SDK und ONNX Runtime 1.24.2 (Microsoft-Build, per `ORT_LIB_LOCATION` + `ORT_PREFER_DYNAMIC_LINK=1` eingebunden).

```powershell
bun install --frozen-lockfile
bun run tauri build --bundles nsis
```

Der GitHub-Actions-Workflow **Windows-Build** baut bei jedem Push einen unsignierten NSIS-Installer und stellt ihn als Artefakt bereit. Weil der Installer nicht signiert ist, zeigt Windows beim ersten Start eine SmartScreen-Warnung („Weitere Informationen“ → „Trotzdem ausführen“).
