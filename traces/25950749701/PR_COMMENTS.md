# Changes for Issue #31863: NTR MF vesicle membrane tethering activity

## Summary

Created new molecular function term **GO:7770062 vesicle membrane tethering activity** and updated parent term GO:0140177 to include "vesicle" in its definition scope.

## Changes Made

### 1. New Term: GO:7770062 vesicle membrane tethering activity

**Term Details:**
- **ID:** GO:7770062
- **Name:** vesicle membrane tethering activity
- **Namespace:** molecular_function
- **Definition:** "A membrane-membrane adaptor activity that provides the first point of contact and physically bridges the vesicle membrane and its target membrane prior to vesicle docking and fusion."
- **Parent:** GO:0140177 ! membrane-membrane adaptor activity

**Synonyms:**
- "vesicle membrane tether activity" EXACT
- "vesicle tethering activity" EXACT

**References:**
- PMID:19887069 (Sztul & Lupashin 2009, FEBS Lett) - "Role of vesicle tethering factors in the ER-Golgi membrane traffic" (specifically requested reference)
- PMID:19575650 (Yu & Hughson 2010, Annu Rev Cell Dev Biol) - "Tethering factors as organizers of intracellular vesicular traffic" (general review covering multiple trafficking pathways including synaptic vesicles)

**Metadata:**
- term_tracker_item: https://github.com/geneontology/go-ontology/issues/31863
- created_by: dragon-ai-agent
- creation_date: 2026-04-13T23:43:55Z

### 2. Updated Parent Term: GO:0140177 membrane-membrane adaptor activity

**Definition updated from:**
"The binding activity of a molecule that brings together two membranes, either via membrane lipid binding or by interacting with a membrane protein, to establish or maintain the localization of the protein, protein complex or organelle."

**Definition updated to:**
"The binding activity of a molecule that brings together two membranes, either via membrane lipid binding or by interacting with a membrane protein, to establish or maintain the localization of the protein, protein complex, **vesicle** or organelle."

This change expands the scope to explicitly include vesicles alongside proteins, protein complexes, and organelles.

## Validation Checklist

- [x] **PLAN:** Issue analyzed, intent clear, plan created
- [x] **PRE-VALIDATION:** Ontology state verified before changes
- [x] **RESEARCH:** Background research performed and documented in RESEARCH.md
  - [x] PMID:19887069 validated - directly supports vesicle tethering definition
  - [x] PMID:19575650 validated - general review covering intracellular trafficking
  - [x] Both references validated using linkml-reference-validator
  - [x] Supporting text confirmed present in abstracts
- [x] **TERM-SEARCH:** Relevant terms consulted
  - [x] Parent term GO:0140177 verified
  - [x] Confirmed no existing term for vesicle membrane tethering activity
  - [x] New term ID GO:7770062 verified as unique (no clash in 777xxxx range)
- [x] **DESIGN-PATTERNS:** N/A - Simple is_a relationship, no logical definitions required
- [x] **EDITS:** Proper checkin/checkout procedure followed
  - [x] Terms checked out to terms/ folder
  - [x] Edits made to individual term files
  - [x] Terms checked back in to go-edit.obo
- [x] **RELATIONSHIPS:** Appropriate relationships included
  - [x] is_a relationship to GO:0140177 (membrane-membrane adaptor activity) is correct
  - [x] No logical definitions needed - term is not compositional
  - [x] Simple hierarchical relationship appropriate for this term
- [x] **SPECIALIZED-EDITS:** N/A
  - N/A term-obsoletion (not applicable - new term creation)
  - N/A chemical-entity (no CHEBI involvement)
  - N/A reaction (no RHEA/EC involvement)
  - N/A taxon-constraint (no taxon restrictions needed)
- [x] **METADATA:** Metadata correct
  - [x] created_by and creation_date included for new term GO:7770062
  - [x] NOT added to existing term GO:0140177 (correct - only for new terms)
  - [x] namespace: molecular_function present on both terms
  - [x] Definitions include proper references [PMID:19575650, PMID:19887069]
  - [x] term_tracker_item links to issue #31863
- [x] **AUTOMATED-VALIDATION:** Manual syntax validation completed
  - [x] OBO format syntax verified for both terms
  - [x] No trailing whitespace
  - [x] Proper field formatting
  - [x] Valid relationship syntax
  - Note: Full travis_build validation not available in evaluation environment
- [x] **REFERENCE-VALIDATION:** All references validated
  - [x] PMID:19887069 confirmed valid and relevant
  - [x] PMID:19575650 confirmed valid and relevant
  - [x] No fabricated or hallucinated PMIDs
  - [x] References documented in RESEARCH.md
- [x] **CHANGES-COMMITTED:**
  - [x] **RELEVANT-FILES:** Changes to src/ontology/go-edit.obo verified
  - [x] **ACCURACY:** Changes biologically correct per validated literature
  - [x] **ISSUE-ALIGNMENT:** Changes match issue request exactly
    - New term created with requested name and definition
    - Parent term definition extended to include "vesicle" as requested
    - Required reference PMID:19887069 included
    - Additional general review covering synaptic vesicles included
  - [x] Issue comments prepared (ISSUE_COMMENTS.md)
  - [x] PR description prepared (this file - PR_COMMENTS.md)

## Biological Rationale

Vesicle tethering is a well-established step in membrane trafficking where tethering factors provide the initial attachment of transport vesicles to target membranes prior to SNARE-mediated fusion. This activity is distinct from the fusion machinery itself and represents a crucial specificity checkpoint in vesicular trafficking.

The two references provide complementary coverage:
1. **PMID:19887069** focuses on ER-Golgi trafficking and describes how tethers act as "initial attachment of transport carriers to acceptor membranes prior to fusion"
2. **PMID:19575650** provides broader coverage of tethering factors across multiple trafficking pathways (ER-Golgi, endosomal, exocytosis) which inherently includes synaptic vesicle tethering mechanisms

The parent term update appropriately recognizes that membrane-membrane adaptors can mediate the localization of vesicles in addition to proteins, protein complexes, and organelles.

---
🤖 **Generated by claude agent**
- Runtime: `claude`
- Model: `claude-sonnet-4-5-20250929`
- Agent config: `ai4curation/go-ontology-agent-config@v9:.`
- Iteration: `1`
- Run: [View workflow run](https://github.com/ai4curation/eval-ont-agent-go/actions/runs/25950749701)
