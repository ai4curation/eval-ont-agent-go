## Summary

This PR addresses geneontology/go-ontology#31902 by creating three new venom-mediated terms related to inflammatory response and modifying two existing terms to fit into the new hierarchy.

## New Terms

### GO:7770071 — venom-mediated activation of inflammatory response

**Parent:** GO:0035738 (venom-mediated perturbation of biological process) — inferred via logical definition.

**Definition:** "A process in which an organism initiates, promotes, or enhances inflammatory response in another organism via the action of a venom."

**Synonyms:**
- envenomation resulting in positive regulation of inflammatory response in another organism (EXACT)
- envenomation resulting in positive regulation of inflammatory response in other organism (EXACT)
- venom-mediated inflammation (BROAD)

**Logical definition:**
```obo
intersection_of: GO:0035738 ! venom-mediated perturbation of biological process
intersection_of: positively_regulates_in_another_organism GO:0006954 ! inflammatory response
```

**References:** PMID:32024243, PMID:19000915

**Rationale:** This follows the established GO design pattern for venom-mediated "activation" terms, which map to `positively_regulates_in_another_organism` (e.g., GO:0044494, venom-mediated activation of voltage-gated sodium channel activity).

### GO:7770072 — venom-mediated leukocyte infiltration

**Parent:** GO:7770071 (is_a)

**Definition:** "A process by which an organism causes leucocyte infiltration in another organism via the action of a venom."

**Synonyms:**
- envenomation resulting in induction of leucocyte infiltration in another organism (EXACT)
- envenomation resulting in induction of leucocyte infiltration in other organism (EXACT)

**References:** PMID:32024243, PMID:26072684, PMID:19000915

**Rationale:** No corresponding GO term for "leukocyte infiltration" exists as a distinct process for a logical definition, so this term uses a simple is_a relationship to the parent inflammatory response term.

### GO:7770073 — venom-mediated release of inflammatory mediator

**Parent:** GO:7770071 (is_a)

**Definition:** "A process by which an organism causes release of inflammatory mediator in another organism via the action of a venom. Inflammatory mediators may include cytokines or interleukins, for example."

**Synonyms:**
- venom-mediated production of proinflammatory mediator (EXACT)

**References:** PMID:32024243, PMID:26072684

**Rationale:** Like GO:7770072, there is no single GO process term that precisely maps to "release of inflammatory mediator" as a target for a logical definition, so a simple is_a parent relationship is used.

## Modified Terms

### GO:0044398 — venom-mediated edema

- **Changed:** `is_a: GO:0035738` → `is_a: GO:7770071`
- **Added:** `property_value: term_tracker_item` for issue #31902

The reasoner correctly infers GO:0044398 as a subclass of GO:0035738 through the new parent GO:7770071, which itself is logically defined as a subclass of GO:0035738.

### GO:0044480 — venom-mediated mast cell degranulation

- **Added:** `relationship: part_of GO:7770071 ! venom-mediated activation of inflammatory response`
- **Added:** `property_value: term_tracker_item` for issue #31902

Mast cell degranulation is a well-established component of the inflammatory response, making `part_of` the appropriate relationship.

## Validation

- [x] `robot convert` syntax check: **PASS**
- [x] `robot reason` (ELK reasoner): **PASS** — no unsatisfiable classes
- [x] SPARQL QC checks executed (missing namespace, definition constraints, duplicate synonyms, obsolete definitions, trailing whitespace, owldef self-reference, equivalent classes): **ALL PASS**

## Background Research

PMIDs were validated against PubMed:

- **PMID:32024243** — "Inflammatory Reaction Induced by Two Metalloproteinases Isolated from Bothrops atrox Venom..." (Toxins, 2020). Directly supports all three terms; describes SVMP-induced edema, leukocyte accumulation, and TNF-α release.
- **PMID:26072684** — "Inflammatory mediators involved in the paw edema and hyperalgesia induced by Batroxase..." (Int Immunopharmacol, 2015). Supports edema, hyperalgesia, mast cell degranulation, and inflammatory mediator involvement.
- **PMID:19000915** — "BthMP: a new weakly hemorrhagic metalloproteinase from Bothrops moojeni snake venom" (Toxicon, 2009). Supports edema and leukocytic infiltrate.

## Checklist

Following the GO ontology agent guidelines:

- [x] PLAN: Issue analyzed and intent is clear
- [x] PRE-VALIDATION: Current state validated (environment limitation noted; individual checks substituted)
- [x] RESEARCH: Necessary background research performed via web search and PubMed validation
- [x] TERM-SEARCH: Relevant existing terms consulted (GO:0006954, GO:0035738, GO:0044398, GO:0044480)
- [x] DESIGN-PATTERNS: Existing venom-mediated term patterns consulted
- [x] EDITS: Checkin/checkout procedure followed
- [x] RELATIONSHIPS:
  - [x] GO:7770071 logical definition appropriate and not over-specified
  - [x] GO:7770072 and GO:7770073 use simple is_a (no over-specified logical definitions)
  - [x] GO:0044398 is_a changed appropriately
  - [x] GO:0044480 part_of added appropriately
- [x] METADATA:
  - [x] created_by and creation_date added for new terms only
  - [x] term_tracker_item added for all new and modified terms
  - [x] All terms have namespace: biological_process
  - [x] Definitions include validated references
- [x] AUTOMATED-VALIDATION: robot convert + robot reason + SPARQL QC — all pass
- [x] REFERENCE-VALIDATION: All PMIDs validated against PubMed
- [x] CHANGES-COMMITTED: Only src/ontology/go-edit.obo committed

## Files Changed

- `src/ontology/go-edit.obo`

---
🤖 **Generated by opencode agent**
- Runtime: `opencode`
- Model: `togetherai/moonshotai/Kimi-K2.6`
- Agent config: `ai4curation/go-ontology-agent-config@v9:.`
- Iteration: `1`
- Run: [View workflow run](https://github.com/ai4curation/eval-ont-agent-go/actions/runs/25646693954)
