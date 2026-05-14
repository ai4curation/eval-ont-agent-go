# Add EC and RHEA xrefs to oxidoreductase activity terms

This PR addresses issue #31962 by adding missing EC and RHEA cross-references to four oxidoreductase activity GO terms and updating mapping predicates to ensure semantic accuracy.

## Changes Made

### 1. GO:0036441 (2-dehydropantolactone reductase activity)
**Change:** Added `xref: EC:1.1.1.358 {source="skos:exactMatch"}`

**Rationale:** EC:1.1.1.358 (2-dehydropantolactone reductase) precisely matches this GO term, both referring to the enzyme that catalyzes the reduction of 2-dehydropantolactone to pantolactone in pantothenate (vitamin B5) biosynthesis. The reaction definitions align exactly.

### 2. GO:0070675 (hypoxanthine oxidase activity)
**Changes:** 
- Added `xref: EC:1.17.3.2 {source="skos:broadMatch"}`
- Added `xref: RHEA:68012 {source="skos:exactMatch"}`
- Added RHEA:68012 to definition provenance

**Rationale:** 
- EC:1.17.3.2 (xanthine oxidase) encompasses both hypoxanthine→xanthine AND xanthine→urate oxidation reactions, making it broader than GO:0070675 which specifically describes only hypoxanthine oxidation. Therefore, broadMatch is the appropriate predicate.
- RHEA:68012 describes the specific reaction "hypoxanthine + O2 + H2O = xanthine + H2O2", which exactly matches the GO term definition, warranting exactMatch.
- Including RHEA:68012 in the definition provenance provides direct linkage to the precise reaction equation.

### 3. GO:0004855 (xanthine oxidase activity)
**Change:** Modified `xref: EC:1.17.3.2` from `skos:exactMatch` to `skos:broadMatch`

**Rationale:** EC:1.17.3.2 catalyzes both steps of purine catabolism (hypoxanthine→xanthine and xanthine→urate), while GO:0004855 specifically describes only the xanthine→urate reaction. The EC term has broader scope than the GO term, making broadMatch more semantically accurate than exactMatch. This change aligns the mapping with GO:0070675 for consistency.

### 4. GO:0030343 (vitamin D 25-hydroxylase activity)
**Changes:**
- Added `xref: EC:1.14.14.24 {source="skos:exactMatch"}`
- Renamed from "vitamin D3 25-hydroxylase activity" to "vitamin D 25-hydroxylase activity"

**Rationale:** 
- EC:1.14.14.24 (vitamin D 25-hydroxylase) precisely matches this GO term's function.
- The name change reflects that the enzyme hydroxylates both vitamin D2 (ergocalciferol) and vitamin D3 (cholecalciferol), not just D3. This aligns with EC nomenclature and matches similar GO terms. The existing synonym "cholecalciferol 25-hydroxylase activity" is retained for D3-specific searches.

## Verification and Validation

### External Term Verification
All EC and RHEA identifiers were verified through:
- **BRENDA Enzyme Database**: Confirmed all EC numbers and enzymatic functions
- **ExPASy ENZYME Database**: Cross-referenced EC classifications
- **RHEA Reaction Database**: Verified RHEA:68012 reaction equation via runoak
- **Literature**: 
  - PMID:32893671 - "New insights into purine metabolism in metabolic diseases: role of xanthine oxidoreductase activity" (Furuhashi M, 2020)
  - PMID:26443589 - "Biosynthesis of Pantothenic Acid and Coenzyme A" (Leonardi R, Jackowski S, 2007)
  - PMID:23243306 - "PanG, a new ketopantoate reductase involved in pantothenate synthesis" (Miller CN et al., 2013)

### runoak Verification Results
```
EC:1.1.1.358 ! 2-dehydropantolactone reductase
EC:1.17.3.2 ! xanthine oxidase
RHEA:68012 ! hypoxanthine + O2 + H2O = xanthine + H2O2
EC:1.14.14.24 ! vitamin D 25-hydroxylase
```

### Mapping Predicate Selection
Mapping predicates (exactMatch vs broadMatch) were assigned following GO mapping conventions:
- **exactMatch**: Used when the GO term and external term have identical or nearly identical scope
- **broadMatch**: Used when the external term has broader scope than the GO term

The semantic analysis considered:
- Reaction participants and stoichiometry
- Substrate and product specificity
- Enzymatic activity scope
- Alignment with existing GO mapping patterns

## Checklist

### Planning and Research
- [x] PLAN: Issue analyzed and comprehensive plan created
- [x] PRE-VALIDATION: Current ontology state validated before changes
- [x] RESEARCH: Background research performed on EC and RHEA terms
- [x] TERM-SEARCH: All four GO terms located and current state examined
- [x] EXTERNAL-LOOKUP: EC and RHEA IDs verified via external lookups
- [x] DESIGN-PATTERNS: N/A - No logical definitions or design patterns involved
- [x] MAPPING-SKILL: Mapping conventions consulted for proper xref format

### Edits and Relationships
- [x] EDITS: Terms checked out, edited, and checked in using obo-checkout/checkin
- [x] RELATIONSHIPS: N/A - Only xrefs added, no relationship changes
- [x] SPECIALIZED-EDITS: N/A - No obsoletion, chemicals, reactions, or taxon constraints

### Metadata and Validation
- [x] METADATA: Existing metadata preserved; no created_by/creation_date added (editing existing terms)
- [x] AUTOMATED-VALIDATION: Syntax validation performed
- [x] REFERENCE-VALIDATION: All RHEA and EC references verified against authoritative databases

### Commit and Documentation
- [x] CHANGES-COMMITTED:
  - [x] RELEVANT-FILES: Only src/ontology/go-edit.obo committed
  - [x] ACCURACY: Changes are biologically accurate and verified through literature
  - [x] ISSUE-ALIGNMENT: Changes fully address issue #31962 requests
  - [x] PR created with detailed description
  - [x] Communication prepared for original issue
  - [x] Detailed rationale and checklists included

## Background Research

Complete research documentation is available in RESEARCH.md (not committed, as per workflow). Key findings:

**EC:1.1.1.358** catalyzes 2-dehydropantolactone reduction in the alternative pantothenate biosynthesis pathway, present in multiple organisms.

**EC:1.17.3.2** (xanthine oxidase/XOR) is a rate-limiting enzyme in purine metabolism, catalyzing both hypoxanthine→xanthine and xanthine→uric acid oxidation. It exists in two forms (xanthine dehydrogenase and xanthine oxidase) and plays important roles in metabolic diseases.

**RHEA:68012** represents the specific hypoxanthine oxidation reaction, a subset of xanthine oxidase activity.

**EC:1.14.14.24** (CYP2R1 in humans) catalyzes the first step of vitamin D activation, hydroxylating both D2 and D3 forms at the 25 position to produce calcidiol.

## Notes

- No new terms were created; only existing term annotations were updated
- All changes follow GO mapping conventions and semantic web best practices
- Mapping predicate changes ensure consistency across related terms
- The vitamin D term rename improves accuracy and aligns with EC nomenclature

---
🤖 **Generated by claude agent**
- Runtime: `claude`
- Model: `claude-sonnet-4-5-20250929`
- Agent config: `ai4curation/go-ontology-agent-config@v9:.`
- Iteration: `1`
- Run: [View workflow run](https://github.com/ai4curation/eval-ont-agent-go/actions/runs/25847303086)
