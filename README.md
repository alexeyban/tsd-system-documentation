# TSD system documentation

How **TSD** works. TSD is a Windows CE barcode data-collection terminal paired with a desktop exchange server.
Everything here was recovered from the compiled .NET binaries in the application's `bin/Release` folder
alone. No source code, design documents or developers were consulted.

The analysis was produced with **EKOS**, which does deterministic, in-process recovery of compiled .NET/JVM
binaries. It uses no decompiler, source or LLM. Every claim is tagged with how it was obtained: compiled,
observed, graph query or interpretation. Most claims also carry an ECMA-335 metadata-token locator back to
the exact method in the exact build.

## Contents

| Path | What it is |
|---|---|
| [`index.html`](index.html) | Full system documentation in 18 sections: architecture, the exchange cycle, the seven handheld workflows, the action engine, anatomy of one scan, data model, storage format, device integration, configuration reference, risks and dead code, limits of the analysis, and how to reproduce it |
| [`how-it-works.html`](how-it-works.html) | 12-slide overview deck |
| [`evidence/binary-explain/`](evidence/binary-explain/) | Raw `ekos_binary_explain` output for the 22 key types the documentation cites |
| [`evidence/generated/`](evidence/generated/) | EKOS's deterministic reports: README, Architecture, Dependency Risk Report, Onboarding Guide, Findings Memo |
| [`evidence/impact-AddScannedRow.json`](evidence/impact-AddScannedRow.json) | `ekos_impact` result behind the "blast radius" of the scan-record writer |
| `assets/` | Stylesheet, favicon and slide-navigation script the two pages load |

## Viewing

Clone the repo and open `index.html` or `how-it-works.html` in a browser. Both pages are fully offline and
load nothing from the network. The application's user interface is in Russian. The documents quote its
on-screen strings in English translation, and the raw evidence files keep the original Russian constants.

## Subject and numbers

- Input: `github.com/alexeyban/tsd`, `SmartDeviceProject3/SmartDeviceProject2/SmartDeviceProject2/bin/Release`.
  That is 31 files, of which 12 are managed assemblies.
- Recovered: 888 types, 8,327 methods, 10,956 resolved call edges and 174 external I/O boundaries.
  There is no database I/O.
- Ledger: 44,865 objects and 74,353 relationships. Zero LLM calls.
