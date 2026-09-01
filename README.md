# ORPR v0.1 — mapa nawigacyjna

Open Retail Process Reference (ORPR) is an open reference for describing retail processes.
This deliberately narrow v0.1 package contains the navigation map, not the complete process
standard.

## What is included

- one Polish-language navigation map covering 70 identified processes in 22 business areas;
- one additional unnumbered candidate shown separately on the map;
- the content and code license texts, licensing explanation, provenance and integrity manifest;
- a candid list of known limitations.

The map gives each identified process a navigation address and a stable technical identifier. It
does not define the process merely by naming it.

## What is not included

This package does not contain process cards, domain profiles, regulatory mappings, decision logs,
internal working papers, review snapshots or the repository history. It does not claim to provide
complete roles, responsibilities, inputs, outputs, gates, handoffs or an implementation-ready
operating model. See `KNOWN-LIMITATIONS.md` before using the map.

## Files and integrity

`MANIFEST.sha256` records the SHA-256 digest of every payload file except the manifest itself.
After extracting the archive, verify it with a SHA-256 tool compatible with the common
`sha256sum -c MANIFEST.sha256` format.

`PROVENANCE.md` lists the closed source-to-package mapping. Any repository path not listed there
was excluded by default.

## License and attribution

The map and substantive documentation are licensed under Creative Commons Attribution-ShareAlike
4.0 International. The repository's code and tools are licensed under Apache License 2.0. This
package retains both license texts and the explanation in `LICENSING.md` even though it does not
contain the builder source code.

Required attribution:

> Open Retail Process Reference (ORPR), R. Myrta, https://myrta.me/orpr

The canonical address is an attribution identifier. Its availability is not guaranteed by this
pre-publication package and requires a separate publication decision.
