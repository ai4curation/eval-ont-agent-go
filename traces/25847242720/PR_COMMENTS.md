# Summary

Created new molecular function term GO:7770062 "vesicle membrane tethering activity" and updated the definition of parent term GO:0140177 "membrane-membrane adaptor activity" to include vesicle as a localized entity, as requested in issue #31863.

## Changes Made

### 1. New Term: GO:7770062 vesicle membrane tethering activity

**Term stanza:**
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

### 2. Updated Parent Term: GO:0140177 membrane-membrane adaptor activity

**Modified definition:**
- **Before:** "The binding activity of a molecule that brings together two membranes, either via membrane lipid binding or by interacting with a membrane protein, to establish or maintain the localization of the protein, protein complex or organelle."
- **After:** "The binding activity of a molecule that brings together two membranes, either via membrane lipid binding or by interacting with a membrane protein, to establish or maintain the localization of the protein, protein complex, vesicle or organelle."

## Rationale

Vesicle membrane tethering is a critical molecular function in intracellular trafficking, representing the initial contact between transport vesicles and target membranes. This occurs prior to docking (GO:0160321) and fusion events. The term fills a gap in the ontology hierarchy under GO:0140177, which already includes various organelle-specific membrane tethering activities (e.g., mitochondrion-plasma membrane, ER-plasma membrane, peroxisome-mitochondrion).

The biological process counterpart GO:0099022 "vesicle tethering" already exists, and several multiprotein tethering complexes (TRAPP, HOPS, CORVET, GARP, exocyst) are annotated with "capable_of_part_of" relationships to that process. The new molecular function term provides an appropriate activity term for annotation of the individual proteins that execute this function.

## Reference Validation

Both PMIDs were validated using linkml-reference-validator:

**PMID:19887069** - Sztul E, Lupashin V (2009) "Role of vesicle tethering factors in the ER-Golgi membrane traffic." FEBS Lett.
- Specifically requested in original issue for ER-Golgi membrane traffic focus
- States: "A well-accepted role for tethering factors is the initial attachment of transport carriers to acceptor membranes prior to fusion"
- Directly supports the definition

**PMID:19575650** - Yu IM, Hughson FM (2010) "Tethering factors as organizers of intracellular vesicular traffic." Annu Rev Cell Dev Biol.
- Requested as a general review covering synaptic vesicle transport
- Comprehensive review of tethering factors across intracellular trafficking pathways
- States: "Intracellular trafficking entails the budding, transport, tethering, and fusion of transport vesicles"
- Covers broad range of tethering complexes including those relevant to synaptic vesicle trafficking

Full validation details available in RESEARCH.md.

## Validation Checklist

- [x] **PLAN:** Issue analyzed, user intent clear, appropriate solution implemented
- [x] **PRE-VALIDATION:** Ontology structure verified before changes
- [x] **RESEARCH:** Background research performed, PMIDs validated via linkml-reference-validator
  - [x] PMID:19887069 validated and relevant
  - [x] PMID:19575650 validated and relevant
  - [x] Both references directly support the definition
- [x] **TERM-SEARCH:** Relevant ontology terms consulted
  - [x] Parent term GO:0140177 verified as appropriate
  - [x] Sibling terms reviewed (GO:0160190, GO:0160214, GO:0160321, GO:7770065, etc.)
  - [x] Related BP term GO:0099022 vesicle tethering identified
  - [x] Term follows established pattern for children of GO:0140177
- [x] **DESIGN-PATTERNS:** N/A - simple direct is_a relationship, no logical definitions required
- [x] **EDITS:** Changes made to src/ontology/go-edit.obo
  - [x] New term GO:7770062 added with proper structure
  - [x] Parent term GO:0140177 definition updated
- [x] **RELATIONSHIPS:** Appropriate relationships included
  - [x] is_a relationship to GO:0140177 is correct and follows pattern
  - [x] No logical definitions needed (simple term, not compositional)
  - [x] Term appropriately positioned in ontology hierarchy
- [x] **SPECIALIZED-EDITS:** N/A
  - N/A /term-obsoletion (no obsoletions)
  - N/A /chemical-entity (no CHEBI terms involved)
  - N/A /reaction (no RHEA/EC terms involved)
  - N/A /taxon-constraint (no taxon restrictions needed)
- [x] **METADATA:** Metadata correct
  - [x] GO:7770062 has required fields: id, name, namespace, def
  - [x] Definition includes validated PMIDs in proper format
  - [x] Synonyms present with appropriate scope (EXACT)
  - [x] term_tracker_item links to issue #31863
  - [x] created_by and creation_date present (appropriate for NEW term)
  - [x] Namespace is molecular_function (correct)
  - [x] GO:0140177 modified appropriately (no new metadata added to existing term)
- [x] **AUTOMATED-VALIDATION:** Validation approach documented
  - Note: Full travis_build not available in evaluation environment
  - Manual verification performed: syntax correct, no obvious errors
  - Term follows all GO conventions and patterns
- [x] **REFERENCE-VALIDATION:** All PMIDs validated via linkml-reference-validator
  - [x] PMID:19887069 confirmed correct and relevant
  - [x] PMID:19575650 confirmed correct and relevant
  - [x] No fabricated or hallucinated references
- [x] **CHANGES-COMMITTED:**
  - [x] **RELEVANT-FILES:** Changes to src/ontology/go-edit.obo committed
  - [x] **ACCURACY:** Changes are biologically correct, based on validated references
  - [x] **ISSUE-ALIGNMENT:** Changes fully address issue #31863 requirements
  - [x] **PR:** This PR addresses issue #31863
  - [x] **COMMUNICATION:** Issue comments and PR description complete

## Files Modified

- `src/ontology/go-edit.obo` - Added GO:7770062, updated GO:0140177 definition

## Testing

In a full ODK environment, the following validation would be performed:
```bash
cd src/ontology && make travis_build
```

Manual verification confirms:
- Correct OBO syntax
- Proper term structure and formatting
- Valid metadata according to GO standards
- Appropriate relationships and hierarchy placement
- Validated references (no typos or hallucinations)

---
🤖 **Generated by claude agent**
- Runtime: `claude`
- Model: `claude-sonnet-4-5-20250929`
- Agent config: `ai4curation/go-ontology-agent-config@v9:.`
- Iteration: `1`
- Run: [View workflow run](https://github.com/ai4curation/eval-ont-agent-go/actions/runs/25847242720)
