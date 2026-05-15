# PR #<NN> - New Molecular Function Term: Vesicle Membrane Tethering Activity

## Summary of Changes

This PR addresses issue #31863, implementing a new molecular function term for vesicle membrane tethering activity and extending the definition of its parent term.

## Completed Checklist

- [x] **PLAN**: Issue intent is clear—create a new MF term and extend parent definition
- [x] **PRE-VALIDATION**: Ontology is valid prior to changes
- [x] **RESEARCH**: Background research performed using PMID:19887069 (ER-Golgi traffic) and PMID:19575650 (broad tethering review covering synaptic pathways)
- [x] **TERM-SEARCH**: Parent term GO:0140177 identified and verified
- [x] **DESIGN-PATTERNS**: Term follows standard MF compositional pattern (adaptor activity hierarchy)
- [x] **EDITS**: Changes made using standard checkout/checkin procedure in terms/ folder
- [x] **RELATIONSHIPS**: 
  - Single is_a to GO:0140177 (membrane-membrane adaptor activity)
  - No over-specification; relationships are appropriate
  - Logical structure follows existing adaptor activity patterns
- [x] **METADATA**: 
  - New term has created_by: dragon-ai-agent and creation_date: 2026-04-13T23:43:55Z
  - Definition includes proper citations (PMID:19575650, PMID:19887069)
  - term_tracker_item linked to GitHub issue #31863
  - Namespace correctly set to molecular_function
- [x] **AUTOMATED-VALIDATION**: Ontology syntax validated; all required fields present
- [x] **REFERENCE-VALIDATION**: References verified as legitimate PMIDs
- [x] **CHANGES-COMMITTED**: Changes committed to src/ontology/go-edit.obo

## Detailed Changes

### 1. New Term: GO:7770062 - vesicle membrane tethering activity

```obo
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

**Rationale**: 
- Addresses the specific biological process of membrane tethering in vesicle traffic
- Follows the established pattern of child terms specifying the context (vesicle) within the parent adaptor activity hierarchy
- References cover both specific ER-Golgi traffic (PMID:19887069) and broader tethering mechanisms including synaptic vesicle pathways (PMID:19575650)
- Synonyms provide alternative terminology commonly used in the literature

### 2. Modified Term: GO:0140177 - membrane-membrane adaptor activity

**Updated definition** (added "vesicle"):
```
"The binding activity of a molecule that brings together two membranes, either via membrane lipid binding or by interacting with a membrane protein, to establish or maintain the localization of the protein, protein complex, vesicle or organelle."
```

**Rationale**: 
- The original definition implicitly assumed vesicles were localized entities but did not explicitly enumerate them alongside proteins, protein complexes, and organelles
- Expanding the definition to explicitly include vesicles makes the parent term more accurate and comprehensive
- This change accommodates the new child term and other vesicle-related adaptor activities
- The modification is conservative, adding only the missing entity type without altering the overall logical structure

## References

- **PMID:19887069** — Sztul & Lupashin, "Role of vesicle tethering factors in the ER-Golgi membrane traffic," *FEBS Lett*, 2009
  - Focuses on specific mechanisms of ER-Golgi tethering factors (including Uso1/p115, Grp1, and Rud3)
  
- **PMID:19575650** — Yu & Hughson, "Tethering factors as organizers of intracellular vesicular traffic," *Annu Rev Cell Dev Biol*, 2010
  - Comprehensive review covering tethering across multiple trafficking pathways
  - Includes discussion of exocyst (Sec3, Sec15, Exo70) and CATCHR complexes (Munc13 family)
  - Relevant for synaptic vesicle targeting and exocytosis

## Biological Accuracy

The term addresses a critical step in cellular membrane traffic—the initial contact and stabilization between transport vesicles and their target membranes. This process is executed by tethering factor complexes and is essential for both secretory pathway (ER-Golgi, trans-Golgi network) and synaptic transmission. The referenced gene products (Uso1, Grp1, Rud3, Sec3, Exo70, Sec15, Drp1/Sec39) represent the major tethering factors across these contexts, validating the biological scope of the term.

## Testing

- Ontology syntax verified with Python-based OBO format validation
- All required metadata fields present and correctly formatted
- Parent-child relationship properly established
- No namespace violations
- Definition format conforms to GO standards

---
🤖 **Generated by claude agent**
- Runtime: `claude`
- Model: `claude-haiku-4-5-20251001`
- Agent config: `ai4curation/go-ontology-agent-config@v9:.`
- Iteration: `1`
- Run: [View workflow run](https://github.com/ai4curation/eval-ont-agent-go/actions/runs/25897787135)
