# Obsoletion of ergothioneine biosynthetic pathway-variant terms

Closes #32018.

## Summary

Obsoletes the two pathway-variant child terms of GO:0052699 (ergothioneine biosynthetic process) and folds the MetaCyc pathway IDs up onto the parent as `narrowMatch` xrefs. The variant pathways (bacterial vs. fungal) are out of scope for GO and are better represented as GO-CAMs, per the issue request (and the previous discussion in #11163).

### Obsoleted terms (both replaced by GO:0052699)

- **GO:0052704** "ergothioneine biosynthesis from histidine via gamma-glutamyl-hercynylcysteine sulfoxide" — bacterial pathway (MetaCyc:PWY-7255). Issue notes 4 EXP annotations to migrate.
- **GO:0140479** "ergothioneine biosynthesis from histidine via hercynylcysteine sulfoxide synthase" — fungal pathway (MetaCyc:PWY-7550). Issue notes 0 EXP annotations.

Both follow the standard obsoletion pattern: `obsolete` prefix on name, `OBSOLETE.` prefix on def, `comment:` explaining the rationale, `term_tracker_item` pointing to this issue, `is_obsolete: true`, `replaced_by: GO:0052699`. All `is_a`/`relationship`/`intersection_of`/`synonym`/`xref` axioms have been stripped (the Wikipedia xref on GO:0052704 was redundant with the same xref on the parent).

### Edits to other terms

- **GO:0052699** (parent, kept): added `xref: MetaCyc:PWY-7255 {source="skos:narrowMatch"}` and `xref: MetaCyc:PWY-7550 {source="skos:narrowMatch"}`.
- **GO:0044875** (gamma-glutamyl hercynylcysteine sulfoxide synthase activity): `part_of` relationship rewired from GO:0052704 → GO:0052699.
- **GO:0061686** (hercynylcysteine sulfoxide synthase activity): `part_of` relationship rewired from GO:0140479 → GO:0052699.
- **GO:0052707** (already obsolete): `replaced_by` updated from GO:0052704 → GO:0052699 to prevent a chained obsoletion (the `replacedby-obsolete-violation` QC rule would otherwise flag this).

## Rationale

Per the issue and prior discussion (#11163), the two variant pathways differ in their middle enzymatic steps (gamma-glutamylated intermediate vs. direct hercynylcysteine sulfoxide synthase route) but produce the same end product via the same overall transformation (histidine → ergothioneine). GO does not need to enumerate every organism-specific variant of a small-molecule biosynthesis pathway; the gene-product-level evidence for which variant is used is captured by the MF annotations to the constituent enzymes (e.g., GO:0044875 vs. GO:0061686), and downstream pathway context can be expressed in GO-CAMs. Keeping the parent term GO:0052699 with `narrowMatch` xrefs to the two MetaCyc pathways preserves the bridge to MetaCyc without committing GO to maintaining the variants.

## Checklist

- [x] PLAN: issue and prior discussion (#11163) analyzed; intent clear (obsolete two pathway-variant child terms, fold MetaCyc xrefs to parent)
- [x] PRE-VALIDATION: `robot convert`, ELK reasoning, and all 16 SPARQL QC checks pass on go-edit.obo prior to any changes (verified after edits as well, since pre-edit state was clean for these terms)
- [x] RESEARCH: N/A — request is a structural obsoletion of existing well-defined terms; no new biological claims being introduced
- [x] TERM-SEARCH: confirmed all in-ontology references to the two obsoleted terms via `obo-grep.pl`
- [x] DESIGN-PATTERNS: N/A — no new term creation, no new logical-def patterns introduced
- [x] EDITS: performed via `obo-checkout.pl` / `obo-checkin.pl` with files in `terms/`
- [x] RELATIONSHIPS: `part_of` relations rewired on GO:0044875 and GO:0061686 to the surviving parent
- [x] SPECIALIZED-EDITS: /term-obsoletion skill applied — obsolete-term metadata correct, no remaining logical axioms, replaced_by present, chained obsoletion (GO:0052707) fixed
  - /chemical-entity: N/A
  - /reaction: N/A (the affected MF terms remain; their RHEA/EC xrefs are untouched)
  - /taxon-constraint: N/A
- [x] METADATA: `term_tracker_item` added to obsoleted terms pointing at this issue; `created_by`/`creation_date` preserved (not added — these are obsoletions of existing terms, not new terms)
- [x] AUTOMATED-VALIDATION:
  - `robot convert -i go-edit.obo -f obo` — passes
  - `robot reason -r ELK -i go-edit.obo` — passes
  - `robot verify` with all 16 sparql QC checks — all PASS, 0 violations
  - `make travis_build` could not run to completion in this environment (`amm` / Ammonite not installed); this is an env issue independent of the edits
- [x] REFERENCE-VALIDATION: no new PMIDs/ORCIDs introduced; existing PMIDs retained verbatim on the obsoleted-term defs as historical provenance
- [x] CHANGES-COMMITTED:
  - [x] RELEVANT-FILES: only `src/ontology/go-edit.obo` modified and committed
  - [x] ACCURACY: edits are structural; biological accuracy of parent term GO:0052699 unchanged
  - [x] ISSUE-ALIGNMENT: matches the issue request exactly (obsolete the two children, replace_by parent, add the two MetaCyc xrefs as `narrowMatch` on the parent)

## Annotation migration note

Per the issue, GO:0052704 has 4 EXP annotations and GO:0140479 has 0 EXP. These existing annotations should be repointed to GO:0052699 as part of the standard annotation-migration follow-up — handled outside this ontology PR by the usual obsoletion-rewiring pipeline.

---
🤖 **Generated by claude agent**
- Runtime: `claude`
- Model: `claude-opus-4-7`
- Agent config: `ai4curation/go-ontology-agent-config@v9:.`
- Iteration: `1`
- Run: [View workflow run](https://github.com/ai4curation/eval-ont-agent-go/actions/runs/25650711692)
