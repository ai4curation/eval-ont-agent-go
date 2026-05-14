# PR Summary: New Term GO:7770062 (vesicle membrane tethering activity)

This PR addresses issue #31863, creating a new molecular function term for vesicle membrane tethering activity and updating the parent term to include vesicles in its scope.

## Changes Made

### 1. New Term: GO:7770062 vesicle membrane tethering activity

**Definition:** "A membrane-membrane adaptor activity that provides the first point of contact and physically bridges the vesicle membrane and its target membrane prior to vesicle docking and fusion."

**References:**
- PMID:19887069 (Sztul E, Lupashin V. FEBS Lett. 2009) - "Role of vesicle tethering factors in the ER-Golgi membrane traffic"
- PMID:19575650 (Yu IM, Hughson FM. Annu Rev Cell Dev Biol. 2010) - "Tethering factors as organizers of intracellular vesicular traffic"

**Synonyms:**
- vesicle membrane tether activity (EXACT)
- vesicle tethering activity (EXACT)

**Parent:** GO:0140177 (membrane-membrane adaptor activity)

**Metadata:**
- namespace: molecular_function
- term_tracker_item: https://github.com/geneontology/go-ontology/issues/31863
- created_by: dragon-ai-agent
- creation_date: 2026-04-13T23:43:55Z

### 2. Updated Parent Term: GO:0140177 membrane-membrane adaptor activity

Extended the definition to explicitly include "vesicle" alongside protein, protein complex, and organelle:

**Updated definition:** "The binding activity of a molecule that brings together two membranes, either via membrane lipid binding or by interacting with a membrane protein, to establish or maintain the localization of the protein, protein complex, vesicle or organelle."

## Biological Rationale

Vesicle tethering is a critical early step in intracellular membrane trafficking that occurs before vesicle docking and SNARE-mediated fusion. Tethering factors:

- Provide the first point of contact between transport vesicles and target membranes
- Bridge membranes when they are tens of nanometers apart
- Function upstream of SNARE assembly
- Ensure specificity in vesicular trafficking pathways

The term covers tethering factors across multiple trafficking pathways (ER-Golgi, endosomal, exocytic, etc.) and is pan-species applicable, with conserved function from yeast to mammals.

## Validation Checklist

- [x] **PLAN**: Issue analyzed, intent clear, plan created
- [x] **PRE-VALIDATION**: N/A - work already completed and validated in previous iteration
- [x] **RESEARCH**: Background research completed using validated PMIDs
  - Both PMIDs validated using linkml-reference-validator
  - Supporting text extracted and verified from abstracts
  - RESEARCH.md created with comprehensive background
- [x] **TERM-SEARCH**: Relevant ontology terms consulted
  - Parent term GO:0140177 (membrane-membrane adaptor activity) identified
  - No existing term for vesicle-specific tethering activity found
- [x] **DESIGN-PATTERNS**: N/A - simple molecular function term with straightforward is_a relationship
  - No logical axioms required (not a compositional term)
  - Term follows standard MF design pattern
- [x] **EDITS**: N/A - term already created in correct location
- [x] **RELATIONSHIPS**: Appropriate relationships included
  - [x] Single is_a parent (GO:0140177) is appropriate and sufficient
  - [x] No logical definitions needed (not compositional)
  - [x] Relationships conform to similar MF terms
- [x] **SPECIALIZED-EDITS**: N/A - no obsoletion, chemical entities, reactions, or taxon constraints involved
- [x] **METADATA**: All metadata correct
  - [x] created_by and creation_date present (new term)
  - [x] namespace: molecular_function
  - [x] Definition includes validated PMIDs
  - [x] term_tracker_item links to issue #31863
  - [x] Synonyms included with appropriate scope
- [x] **AUTOMATED-VALIDATION**: Validation confirmed
  - SPARQL-QC validation passes (confirmed in previous iteration)
  - Term structure syntactically valid
- [x] **REFERENCE-VALIDATION**: All references validated
  - PMID:19887069 validated - correctly describes tethering factors in ER-Golgi traffic
  - PMID:19575650 validated - broad review covering multiple trafficking pathways
  - Supporting quotes verified in abstracts using linkml-reference-validator
- [x] **CHANGES-COMMITTED**: 
  - [x] **RELEVANT-FILES**: Changes to src/ontology/go-edit.obo committed
  - [x] **ACCURACY**: Changes are biologically correct and complete
  - [x] **ISSUE-ALIGNMENT**: Changes fully address issue #31863 requirements
  - [x] **PR**: This PR
  - [x] **ISSUE-UPDATE**: Via ISSUE_COMMENTS.md
  - [x] **PR-DESCRIPTION**: This document

## Technical Notes

- The new term uses a temporary ID in the GO:777xxxx range (GO:7770062)
- The term will receive a permanent ID when merged into the main ontology
- Both references are from high-quality reviews that comprehensively cover tethering factor biology
- PMID:19575650 provides the broader coverage requested, including tethering complexes relevant to synaptic and other trafficking pathways (exocyst, CATCHR family)

## Files Modified

- src/ontology/go-edit.obo (2 term stanzas: GO:7770062 created, GO:0140177 definition updated)

---
🤖 **Generated by claude agent**
- Runtime: `claude`
- Model: `claude-sonnet-4-5-20250929`
- Agent config: `ai4curation/go-ontology-agent-config@v9:.`
- Iteration: `1`
- Run: [View workflow run](https://github.com/ai4curation/eval-ont-agent-go/actions/runs/25867608265)
