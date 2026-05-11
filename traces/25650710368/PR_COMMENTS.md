## Summary

Obsoletes **GO:0009095** *aromatic amino acid biosynthetic process, prephenate pathway* as requested in issue #32005.

The term is a pre-composed pathway term that should be represented as a GO-CAM model rather than as a single ontology class. Its MetaCyc:PWY-3481 xref is a "superpathway" that combines two more granular pathways:
- MetaCyc:PWY-3462 — L-phenylalanine biosynthesis II → already attached as `narrowMatch` to **GO:0009094** *L-phenylalanine biosynthetic process*
- MetaCyc:PWY-3461 — L-tyrosine biosynthesis II → already attached as `narrowMatch` to **GO:0006571** *L-tyrosine biosynthetic process*

So no MetaCyc xref information is lost from the ontology by this obsoletion. The two granular GO terms above are listed as `consider` candidates for re-annotation.

## Diff (logical content)

Before:
```
[Term]
id: GO:0009095
name: aromatic amino acid biosynthetic process, prephenate pathway
namespace: biological_process
def: "The chemical reactions and pathways resulting in the formation of phenylalanine and tyrosine from other compounds, including chorismate, via the intermediate prephenate." [GOC:mah, ISBN:0471331309, MetaCyc:PWY-3481]
synonym: "aromatic amino acid family anabolism, prephenate pathway" EXACT []
synonym: "aromatic amino acid family biosynthetic process via prephenate" EXACT [GOC:pr]
synonym: "aromatic amino acid family biosynthetic process via prephenate(2-)" EXACT [GOC:pr]
synonym: "aromatic amino acid family formation, prephenate pathway" EXACT []
synonym: "aromatic amino acid family synthesis, prephenate pathway" EXACT []
xref: MetaCyc:PWY-3481
is_a: GO:0009073 ! aromatic amino acid biosynthetic process
intersection_of: GO:0009058 ! biosynthetic process
intersection_of: has_intermediate CHEBI:57852 ! prephenate(2-)
intersection_of: has_primary_output CHEBI:33856 ! aromatic amino acid
property_value: term_tracker_item "https://github.com/geneontology/go-ontology/issues/31091" xsd:anyURI
```

After:
```
[Term]
id: GO:0009095
name: obsolete aromatic amino acid biosynthetic process, prephenate pathway
namespace: biological_process
def: "OBSOLETE. The chemical reactions and pathways resulting in the formation of phenylalanine and tyrosine from other compounds, including chorismate, via the intermediate prephenate." [GOC:mah, ISBN:0471331309, MetaCyc:PWY-3481]
comment: This term was obsoleted because it is a pre-composed term that should be represented as a GO-CAM model. MetaCyc:PWY-3481 is a superpathway combining L-phenylalanine biosynthesis II (MetaCyc:PWY-3462) and L-tyrosine biosynthesis II (MetaCyc:PWY-3461); these component pathway xrefs are already present as narrowMatch on GO:0009094 (L-phenylalanine biosynthetic process) and GO:0006571 (L-tyrosine biosynthetic process) respectively.
property_value: term_tracker_item "https://github.com/geneontology/go-ontology/issues/32005" xsd:anyURI
is_obsolete: true
consider: GO:0009094
consider: GO:0006571
```

## Impact analysis

- **Ontology-internal references to GO:0009095**: none. `obo-grep.pl GO:0009095 src/ontology/go-edit.obo` returned only the term stanza itself. No `is_a`, `relationship`, `intersection_of`, `replaced_by`, or `consider` from any other term points at this ID. No rewiring required.
- **External xrefs / mappings**: the only xref was MetaCyc:PWY-3481. As noted above, no replacement term should receive this xref because PWY-3481 is the superpathway, and its component pathways are already correctly placed on the two more granular terms. The xref is left in the definition provenance as historical record but not preserved as an `xref:` tag.
- **Annotations**: per the issue body, 4 EXP annotations exist (UniProt × 2, TAIR × 1, MTBBASE × 1). The originator's recommendations are summarised in `consider:` (GO:0009094 / GO:0006571). Annotation review/migration is handled in the go-annotation tracker per standard obsoletion procedure and is outside the scope of this PR.

## Checklist

- [x] **PLAN** — Issue and comments reviewed; intent (obsolete GO:0009095 with consider terms GO:0009094 / GO:0006571) is unambiguous.
- [x] **PRE-VALIDATION** — `robot convert` on `go-edit.obo` parsed cleanly before edits.
- [N/A] **RESEARCH** — Not required; the requester provided full rationale and consider candidates.
- [x] **TERM-SEARCH** — Confirmed GO:0009094 and GO:0006571 exist, and that no other term references GO:0009095.
- [N/A] **DESIGN-PATTERNS** — Not applicable for an obsoletion that removes logical axioms.
- [x] **EDITS** — Used `obo-checkout.pl` / `obo-checkin.pl` on `terms/GO_0009095.obo`.
- [x] **RELATIONSHIPS** — All `is_a` / `intersection_of` axioms stripped (correct for an obsolete term).
- [x] **SPECIALIZED-EDITS** — `/term-obsoletion` skill followed. Obsolete term has no logical axioms, no synonyms, has obsolete-prefixed name and `OBSOLETE.` definition, comment with rationale, term_tracker_item to #32005, `consider:` tags.
- [x] **METADATA** — `is_obsolete: true`, `consider` × 2, `term_tracker_item` updated to #32005, comment with rationale, namespace retained.
- [x] **AUTOMATED-VALIDATION**:
  - `robot convert -i go-edit.obo -f obo` — PASS (clean parse).
  - `robot reason -r ELK -i go-edit.obo` — PASS (no unsatisfiable classes introduced).
  - `robot verify` against 16 SPARQL QC queries (equivalent-classes, trailing-whitespace, owldef-self-reference, synonym-label-match, replacedby-obsolete, replacedby-namespace, missing-namespace, duplicate-exact-synonym, duplicate-synonym, non-IRI-value, non-anyURI-value, obsolete-definition, definition-constraints, one-to-one-xrefs-by-subject, one-to-one-xrefs-by-value, xref-syntax) — all PASS, 0 violations.
  - `robot verify` against `obsolete-reference-violation.sparql` — PASS (no live references to obsoleted term).
  - Full `make travis_build` could not be run end-to-end because `amm` (Ammonite) is not available in this sandbox; the SPARQL + reasoning checks above cover the substantive validation pieces.
- [N/A] **REFERENCE-VALIDATION** — No new references introduced.
- [x] **CHANGES-COMMITTED** — Only `src/ontology/go-edit.obo` committed.

## Out of scope (curator follow-up per checklist in the issue)

- Annotation Review spreadsheet
- go-annotation review ticket
- Obsoletion announcement / go-friends notification
- IEA / external-mapping check

---
🤖 **Generated by claude agent**
- Runtime: `claude`
- Model: `claude-opus-4-7`
- Agent config: `ai4curation/go-ontology-agent-config@v9:.`
- Iteration: `1`
- Run: [View workflow run](https://github.com/ai4curation/eval-ont-agent-go/actions/runs/25650710368)
