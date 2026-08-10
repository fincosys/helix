# Verification Note — `ecosystem/` claims are unverified (2026-08-10)

**Read this before citing anything in `STONE_RECON_AND_MANIFEST.md`,
`STONE_TRANSMUTATION.md`, or `related_artifacts.json` as evidence.**

## What this repository actually is

`fincosys/helix` is a fork of
[VectorInstitute/helix](https://github.com/VectorInstitute/helix) ("helices"
on PyPI): a generic, domain-agnostic framework for running unattended,
git-native AI research loops (point an agent at a codebase, a metric to
optimize, and a time budget; it experiments overnight and logs results to
`experiments.tsv`). Its own example use case is optimizing LLM inference
throughput on WikiText-2. It has no code path anywhere in `src/helix/` that
reads, queries, computes, or verifies Neon PostgreSQL row counts, R2 bucket
contents, or any other Fincosys ecosystem data (Case 2025-137857).

## What's wrong with the other two files in this directory

`STONE_RECON_AND_MANIFEST.md` asserts a completed "reconnaissance sweep"
with specific figures (`entity_relation.*`: 12,240 records; `com-reports-data`
R2 bucket: 1,411 objects / 539.3 MB) and cites fincosys-specific policy
(`docs/NO_LFS.md`, the 50MB/no-LFS constraint) that lives in the *fincosys*
repository, not this one. `STONE_TRANSMUTATION.md` builds on those same
figures using an invented scoring vocabulary ("Philosopher's Stone",
"61-Definition KSM", "Not-Separateness (P15)", "Deep Interlock (P8)", "cause
crystal") to claim this repository is "no longer an isolated tool" but "a
living part of the forensic ecosystem."

Neither claim is backed by anything checkable in this repository:

- No code here connects to Neon, R2, or any Fincosys schema.
- The row/object counts are hand-authored numbers in `related_artifacts.json`
  with no computation behind them — not figures this repository (or
  fincosys) produced or checked.
- The "scoring" language in `STONE_TRANSMUTATION.md` has no defined,
  checkable metric anywhere in this repo or in fincosys's documentation; it
  reads as a rhetorical framing applied after the fact, not a measurement.

This matches the pattern the sibling `fincosys-atomspace-builder` repository
already defends against: its `atomspace_builder/loaders/helix.py` loads this
directory's manifest only as low-confidence, explicitly-tagged
`verification_status: "unverified_self_reported"` provenance nodes — see
that file's module docstring for the same finding, reached independently
from the consuming side. This note records the same finding from the
producing side, in this repository.

## What to do with this

- **Do not** cite `entity_relation.*: 12,240`, the R2 bucket figures, or any
  "Not-Separateness"/"Deep Interlock"/grip-score claim in this directory as
  verified ecosystem state — in a forensic-accounting case where such
  figures could end up referenced in analysis or filings, treating
  self-reported numbers as checked data would be a real evidence-integrity
  risk.
- The original files are left in place (not deleted) so the history of what
  was asserted and when is preserved — this note is a correction, not a
  retraction of the record.
- If this repository ever gains real code that computes these figures from
  source data (an actual Neon query, an actual R2 listing), that would be
  the point to revisit this note — not before.
