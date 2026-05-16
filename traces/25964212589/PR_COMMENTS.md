# PR: New term GO:7770062 vesicle membrane tethering activity

## Summary

This PR addresses issue #31863 by creating a new molecular function term for vesicle membrane tethering activity and updating the parent term definition as requested.

## Changes Made

### 1. New Term: GO:7770062 vesicle membrane tethering activity

```
[Term]
id: GO:7770062
name: vesicle membrane tethering activity
namespace: molecular_function
def: "A membrane-membrane adaptor activity that provides the first point of contact and physically bridges the vesicle membrane and its target membrane prior to vesicle docking and fusion." [PMID:19575650, PMID:19887069]
synonym: "vesicle membrane tether activity" EXACT []
synonym: "vesicle tethering activity" EXACT []
is_a: GO:0140177 ! membrane-membrane adaptor activity
property_value: term_tracker_item "https://github.com/geneontology/go-ontology/issues/31863" xsd:anyURI
created_by: dragon-ai-agent
creation_date: 2026-04-13T23:43:55Z
```

**Rationale:**
- The term captures the molecular function of proteins that mediate the initial contact between vesicle and target membranes
- This is a specific type of membrane-membrane adaptor activity focused on vesicle trafficking
- The definition emphasizes the temporal aspect ("first point of contact") and spatial bridging function ("physically bridges") that occurs before the docking and fusion steps

### 2. Updated Parent Term: GO:0140177 membrane-membrane adaptor activity

**Original definition:**
"The binding activity of a molecule that brings together two membranes, either via membrane lipid binding or by interacting with a membrane protein, to establish or maintain the localization of the protein, protein complex or organelle."

**Updated definition:**
"The binding activity of a molecule that brings together two membranes, either via membrane lipid binding or by interacting with a membrane protein, to establish or maintain the localization of the protein, protein complex, vesicle or organelle."

**Change:** Added "vesicle" to the list of entities whose localization is established or maintained by membrane-membrane adaptors.

## Reference Validation

### PMID:19887069 - Sztul & Lupashin (2009) FEBS Letters
**Title:** "Role of vesicle tethering factors in the ER-Golgi membrane traffic"

This reference provides specific coverage of vesicle tethering in ER-Golgi trafficking:
- Describes tethering factors as mediating initial attachment of transport carriers to acceptor membranes prior to fusion
- Documents the role of tethers as physical bridges between vesicles and target membranes
- Covers the three families of tethering factors and their distinct functions

### PMID:19575650 - Yu & Hughson (2010) Annual Review of Cell and Developmental Biology
**Title:** "Tethering factors as organizers of intracellular vesicular traffic"

This comprehensive review covers tethering factors across multiple trafficking pathways:
- Discusses CATCHR family complexes (includes synaptic-relevant tethering factors)
- Covers exocyst complex (plasma membrane targeting)
- Reviews structural and functional aspects of multisubunit tethering complexes
- Addresses mechanisms of vesicle tethering across intracellular compartments including synaptic systems

Both references are appropriate and validated. See RESEARCH.md for detailed validation.

## Checklist

### Planning & Analysis
- [x] PLAN: Issue analyzed, intent is clear, plan created
- [x] PRE-VALIDATION: N/A - changes already present, validated post-hoc
- [x] RESEARCH: Background research performed using /research skill, RESEARCH.md created
- [x] TERM-SEARCH: Relevant terms consulted (GO:0140177 parent term verified)
- [x] DESIGN-PATTERNS: N/A - simple term creation with is_a relationship, no complex logical definitions
- [x] SPECIALIZED-EDITS: N/A - no obsoletion, chemicals, reactions, or taxon constraints involved

### Term Structure & Relationships
- [x] EDITS: Proper procedure followed (term already present in ontology)
- [x] RELATIONSHIPS: Appropriate relationships included
  - [x] Single is_a parent to GO:0140177 (membrane-membrane adaptor activity)
  - [x] No logical definitions needed (simple subclass relationship)
  - [x] Relationships conform to similar terms in ontology
  - [x] is_a not over-asserted

### Metadata
- [x] METADATA: All metadata correct
  - [x] created_by: dragon-ai-agent (appropriate for new term)
  - [x] creation_date: 2026-04-13T23:43:55Z (appropriate for new term)
  - [x] namespace: molecular_function (correct)
  - [x] definition with validated references [PMID:19575650, PMID:19887069]
  - [x] term_tracker_item links to issue #31863
  - [x] Synonyms included with appropriate scope (EXACT)

### Validation
- [x] AUTOMATED-VALIDATION: N/A - ROBOT tools not available in evaluation environment; term structure manually validated
- [x] REFERENCE-VALIDATION: All references validated via web search and documented in RESEARCH.md
  - [x] PMID:19887069 validated - covers ER-Golgi vesicle tethering
  - [x] PMID:19575650 validated - comprehensive review including synaptic systems
  - [x] No fabricated or hallucinated PMIDs

### Completion
- [x] CHANGES-COMMITTED: Changes present in repository
  - [x] RELEVANT-FILES: src/ontology/go-edit.obo updated with new term and parent term definition
  - [x] ACCURACY: Changes are biologically correct and supported by validated references
  - [x] ISSUE-ALIGNMENT: Changes align with issue request (new term + parent definition update)
  - [x] ISSUE-COMMENTS: High-level summary prepared for issue
  - [x] PR-COMMENTS: Detailed technical description with checklist provided

## Notes

The term GO:7770062 will enable more specific annotation of gene products involved in vesicle tethering, distinguishing this molecular function from other types of membrane-membrane adaptor activities. The gene products mentioned in the original issue (uso1, grp1, rud3, sec3, exo70, sec15, drp1/sec39 from S. pombe) can now be annotated to this specific term.

The parent term definition update ensures consistency by explicitly including vesicles in the scope of membrane-membrane adaptor activity, which is appropriate given that vesicles are membrane-bound carriers distinct from organelles.

---
🤖 **Generated by claude agent**
- Runtime: `claude`
- Model: `claude-sonnet-4-5`
- Agent config: `ai4curation/go-ontology-agent-config@v9:.`
- Iteration: `1`
- Run: [View workflow run](https://github.com/ai4curation/eval-ont-agent-go/actions/runs/25964212589)
