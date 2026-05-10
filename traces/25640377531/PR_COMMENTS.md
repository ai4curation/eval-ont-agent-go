# PR Comments - Issue #27593: Ferric Iron Reductase Terminology Refinement

## Changes Summary

This PR addresses the request to distinguish between general ferric iron reductase activity and specifically siderophore/chelate-dependent reductase activity, enabling accurate annotation of the Frp1/Fip1-Fio1 system in fission yeast.

## Implementation Details

### 1. New Term: GO:7770068 - ferric iron reductase activity

**Type**: Molecular Function (catalytic activity)
**Reaction**: `2 Fe3+ + NADP+ + H+ = 2 Fe2+ + NADPH`
**RHEA**: 71767 (skos:exactMatch)
**EC**: 1.16.1.- (skos:broadMatch)
**Parent**: GO:0016722 (oxidoreductase activity, acting on metal ions)

**References**:
- PMID:8321236 - Roman et al. (1993) "The fission yeast ferric reductase gene frp1+ is required for ferric iron uptake and encodes a protein that is homologous to the gp91-phox subunit of the human NADPH phagocyte oxidoreductase"
- PMID:34614242 - Beaudoin et al. (2021) "Fission yeast RNA-binding proteins Puf2 and Puf4 are involved in repression of ferrireductase Frp1 expression in response to iron"
- PMID:39940646 - Amadei et al. (2025) "The Ferroxidase–Permease System for Transport of Iron Across Membranes: From Yeast to Humans"

**Metadata**:
- term_tracker_item: https://github.com/geneontology/go-ontology/issues/27593
- created_by: dragon-ai-agent
- creation_date: 2026-05-10T00:00:00Z

**Rationale**: This general ferric iron reductase term encompasses reduction of both chelated and unchelated Fe3+, distinguishing it from the more specific ferric-chelate reductase activity. It serves as a parent term for GO:0000293.

### 2. Updated Term: GO:0000293 - ferric-chelate reductase activity

**Definition Change**:
- **Before**: "Catalysis of the reaction: 2 Fe3+-siderophore + electron donor = 2 Fe2+-siderophore + electron acceptor."
- **After**: "Catalysis of the reaction: 2 Fe3+-chelate + electron donor = 2 Fe2+-chelate + electron acceptor."

**Rationale for definition change**: The term now correctly uses "chelate" to denote the broader class of chelating agents (including siderophores, citrate, EDTA, and other iron chelates), rather than limiting it to siderophores specifically. This reflects the actual substrate specificity of ferric-chelate reductases. The change is made on both substrate and product sides for chemical consistency.

**Hierarchy Changes**:
- **Added**: `is_a: GO:7770068 ! ferric iron reductase activity`
- **Retained**: `is_a: GO:0016722 ! oxidoreductase activity, acting on metal ions` (will be inferred as a redundant relationship)
- **Added**: `property_value: term_tracker_item "https://github.com/geneontology/go-ontology/issues/27593"`

**Impact on child terms**:
- GO:0052851 (ferric-chelate reductase (NADPH) activity): No changes needed
  - Retains `is_a: GO:0000293` and `is_a: GO:0016723`
  - New inheritance path: GO:0052851 → GO:0000293 → GO:7770068 → GO:0016722
- GO:0140618 (ferric-chelate reductase (NADH) activity): No changes needed
  - Same inheritance pattern as GO:0052851

## Validation Checklist

- [x] PLAN: Issue intent analyzed and plan created
- [x] PRE-VALIDATION: Ontology parses correctly with obo-grep.pl
- [x] RESEARCH: References verified using /research skill
  - PMID:8321236 - Original frp1+ characterization (Roman et al. 1993)
  - PMID:34614242 - Frp1 regulation by Puf2/Puf4 (Beaudoin et al. 2021)
  - PMID:39940646 - Ferroxidase-permease system review (Amadei et al. 2025)
  - RHEA:71767 - Ferric iron reduction reaction confirmed by pgaudet
- [x] TERM-SEARCH: Relevant terms located and examined
  - GO:0000293 (parent term being updated)
  - GO:0052851, GO:0140618 (child terms, verified no direct changes needed)
  - GO:0016722, GO:0016723 (parent hierarchy verified)
- [x] DESIGN-PATTERNS: Hierarchy and relationships conform to oxidoreductase activity patterns
  - New term properly classified under GO:0016722
  - Definition and reaction specification follow GO conventions
  - No logical definitions (intersection_of) needed as this is not a compositional design pattern
- [x] EDITS: Terms properly checked out, edited, and checked in using standard procedure
- [x] RELATIONSHIPS: Hierarchy and relationships appropriate
  - GO:7770068 parent: GO:0016722 (general metal oxidoreductase)
  - GO:0000293 parent: GO:7770068 (specific chelate-dependent subtype)
  - Child terms retain their relationships through GO:0000293
- [x] METADATA: Metadata complete
  - New term includes created_by and creation_date
  - Both terms include term_tracker_item for issue #27593
  - Definition includes proper RHEA and PMID references
- [x] AUTOMATED-VALIDATION: Basic syntax validation passed
  - File parses correctly with obo-grep.pl
  - All references present and properly formatted
  - No syntax errors detected
- [x] REFERENCE-VALIDATION: All PMIDs verified using /research skill
  - All citations are correct and relevant
  - No hallucinated or typo PMIDs
- [x] CHANGES-COMMITTED: Changes committed with detailed message

## Design Pattern Justification

The new hierarchy follows GO's oxidoreductase activity design patterns:

**Pattern**: Catalytic activity terms with specific substrates and cofactors
- Parent terms specify cofactor type or electron acceptor
- Child terms add substrate specificity
- Terms at same level of specificity share common parent

**Hierarchy**: 
```
GO:0016722 (oxidoreductase activity, acting on metal ions)
    └── GO:7770068 (ferric iron reductase activity)
        └── GO:0000293 (ferric-chelate reductase activity)
            ├── GO:0052851 (ferric-chelate reductase (NADPH) activity)
            └── GO:0140618 (ferric-chelate reductase (NADH) activity)
```

**Precedent**: Similar hierarchy seen in other ferric reductase and iron-handling terms
- GO:0004322 (ferroxidase activity) - inverse reaction with oxygen acceptor
- GO:0052851/0140618 - specific cofactor versions of parent term

## Notes

- The definition change for GO:0000293 maintains backward compatibility in intent while improving accuracy. Existing annotations using this term will remain valid and more accurate (most annotated terms are likely specific siderophore reductases that are also chelate reductases).
- The new parent term enables proper annotation of non-siderophore chelate reductases and general ferric iron reductases.
- The Frp1/Fip1-Fio1 system, which was the original driver of this issue, can now be accurately annotated with GO:7770068 (or potentially created as a child term if cofactor specificity becomes important in the future).

---
🤖 **Generated by claude agent**
- Runtime: `claude`
- Model: `claude-haiku-4-5-20251001`
- Agent config: `ai4curation/go-ontology-agent-config@v9:.`
- Iteration: `1`
- Run: [View workflow run](https://github.com/ai4curation/eval-ont-agent-go/actions/runs/25640377531)
