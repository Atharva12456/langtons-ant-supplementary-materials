# Langton's Ant Supplementary Materials

Public repository: [https://github.com/Atharva12456/langtons-ant-supplementary-materials](https://github.com/Atharva12456/langtons-ant-supplementary-materials).
The versioned snapshot is [v1.0.0](https://github.com/Atharva12456/langtons-ant-supplementary-materials/releases/tag/v1.0.0).

Suggested citation: Atharva Jillhewar (2026), *Finite-Support Periodic Highways
of Langton's Ant: Supplementary Materials*, version 1.0.0. https://github.com/Atharva12456/langtons-ant-supplementary-materials.
Machine-readable citation metadata is in [CITATION.cff](CITATION.cff).

| Folder | Contents |
|---|---|
| [01 Report](01_Report/report.pdf) | Report PDF and [LaTeX source](01_Report/report.tex) |
| [02 Proof reference](02_Proof_reference/proof_reference.pdf) | Detailed reference PDF and [LaTeX source](02_Proof_reference/proof_reference.tex) |
| [03 Research notes](03_Research_notes/README.md) | Eight topic files, 150 main notes, 12 linked supporting notes and source archive |
| [04 Reproduction](04_Reproduction/reproduction.zip) | Selected programs, certificates, Lean modules and bounded-check outputs |
| [05 Raw records](05_Raw_records/raw_search_records.zip) | Original computation records and supporting files |

Read the current report first, then the detailed reference and the research-note
index. The source archive retains the individual notes and their original paths;
the topic files provide a shorter list of documents to navigate. Individual
notes and numerical evidence remain available in the archives.

The report and detailed reference PDFs were compiled from the accompanying
LaTeX sources. The report has 23 physical pages, including 20 numbered
content pages; the detailed reference has 94 pages.

The detailed reference and notes contain dated restricted and superseded
approaches. All ten growth-eight drift orbits retain open cases. Growth at least
twelve and the universal highway conjecture are not proved. The growth-four
exclusion includes a computer-assisted primitive classification; the Lean
formalization has explicit remaining hypotheses.

For reproduction, extract all three ZIPs into the same empty directory, preserving
their paths, and read REPRODUCE.md. The four delivered current-report checks and
the bounded Lemma M check passed. The supplied phase-rounding checker also
passed against all 57 recorded inputs, reproducing its saved audit exactly.
Long searches and Lean builds were not rerun.
Later exploratory notes also name run directories in plain text; their entire
execution environment is outside this selected reproduction package.

The raw archive preserves 2,256 original records and supporting files, mostly
JSON shards. Its original manifest and contents remain unchanged. The package
manifests identify files by SHA-256; CONTENTS.json identifies this organized
folder. [SCOPE.md](SCOPE.md) describes proof dependencies and the extent of the
computational checks.
