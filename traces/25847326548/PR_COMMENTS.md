# Reparent 49 EC:1.14.14.x cytochrome P450 terms to correct EC hierarchy

## Summary

This PR addresses issue #31967 by reparenting 49 cytochrome P450 monooxygenase activity terms from GO:0016709 to GO:0016712, aligning their GO hierarchy with the IUBMB 2018 EC classification update.

## Background

The affected terms carry EC:1.14.14.x xrefs (with skos:exactMatch mappings), indicating they belong to EC sub-subclass 1.14.14 (oxidoreductases acting on paired donors with reduced flavin/flavoprotein as one donor). However, they were previously classified under GO:0016709, which maps to EC:1.14.13.- (oxidoreductases with NAD(P)H as one donor). This created a hierarchy inconsistency where the terms' EC codes were not in the same sub-subclass as their GO parent's EC code.

## Changes Made

Replaced `is_a: GO:0016709` with `is_a: GO:0016712` for all 49 terms:

- **Old parent**: GO:0016709 "oxidoreductase activity, acting on paired donors, with incorporation or reduction of molecular oxygen, NAD(P)H as one donor, and incorporation of one atom of oxygen" (EC:1.14.13.-)
- **New parent**: GO:0016712 "oxidoreductase activity, acting on paired donors, with incorporation or reduction of molecular oxygen, reduced flavin or flavoprotein as one donor, and incorporation of one atom of oxygen" (EC:1.14.14.-)

For terms with multiple parent classes (e.g., GO:0008398 which is also a demethylase), only the specific is_a relationship to GO:0016709 was modified; all other relationships were preserved.

## Affected Terms (49)

GO:0004506, GO:0008398, GO:0010295, GO:0016710, GO:0016711, GO:0018664, GO:0033772, GO:0033775, GO:0033777, GO:0033781, GO:0036189, GO:0036201, GO:0036202, GO:0036204, GO:0036209, GO:0047082, GO:0047083, GO:0047084, GO:0047087, GO:0047088, GO:0047089, GO:0047957, GO:0048000, GO:0050591, GO:0050592, GO:0050593, GO:0050594, GO:0050596, GO:0050597, GO:0050598, GO:0102001, GO:0102002, GO:0102068, GO:0102170, GO:0102289, GO:0102320, GO:0102375, GO:0102556, GO:0102557, GO:0102596, GO:0102597, GO:0102598, GO:0102684, GO:0102811, GO:0102876, GO:0102934, GO:0102995, GO:0106144, GO:0106149

## Technical Details

### Procedure
1. Verified current state: all 49 terms had `is_a: GO:0016709` and EC:1.14.14.x xrefs
2. Confirmed target parent GO:0016712 exists with `xref: EC:1.14.14.-`
3. Used obo-checkout.pl to check out all 49 terms
4. Performed batch replacement of is_a relationships
5. Used obo-checkin.pl to update src/ontology/go-edit.obo
6. Verified changes: confirmed all terms now have GO:0016712 as parent

### Files Modified
- `src/ontology/go-edit.obo`: 49 is_a relationships updated (49 insertions, 49 deletions)

## Validation

Manual verification confirmed:
- All 49 terms now have `is_a: GO:0016712` 
- All 49 terms retain their EC:1.14.14.x xrefs
- Terms with multiple parents (e.g., GO:0008398) retained their other is_a relationships
- No terms still reference GO:0016709 as a parent

Note: Automated validation tools (robot, amm) were not available in the evaluation environment. Standard travis_build validation should be performed by reviewers.

## Checklist

- [x] PLAN: Issue analyzed, intent clear, plan created
- [x] PRE-VALIDATION: Ontology file accessible and in expected location
- [N/A] RESEARCH: Not required for this administrative reclassification
- [x] TERM-SEARCH: Verified current parent relationships and target parent structure
- [N/A] DESIGN-PATTERNS: Not applicable for simple reparenting
- [x] EDITS: Proper checkout/checkin procedure followed
  - [x] Used obo-checkout.pl to extract terms to terms/ folder
  - [x] Modified is_a relationships
  - [x] Used obo-checkin.pl to update go-edit.obo
- [x] RELATIONSHIPS: Appropriate relationships maintained
  - [x] Only the specific GO:0016709 is_a relationship was modified
  - [x] Other is_a relationships preserved for multi-parent terms
  - [x] No other relationships affected
- [N/A] SPECIALIZED-EDITS: Not required (no obsoletions, CHEBI terms, reactions, or taxon constraints)
- [N/A] METADATA: No metadata changes required (existing terms only)
- [x] AUTOMATED-VALIDATION: Manual verification performed
  - [x] All 49 terms confirmed to have new parent GO:0016712
  - [x] No terms retain old parent GO:0016709
  - [x] EC xrefs preserved
- [N/A] REFERENCE-VALIDATION: No new references introduced
- [x] CHANGES-COMMITTED
  - [x] RELEVANT-FILES: Only src/ontology/go-edit.obo committed
  - [x] ACCURACY: Changes align with IUBMB 2018 EC reclassification
  - [x] ISSUE-ALIGNMENT: Changes directly address issue #31967
  - [x] PR description includes detailed rationale and complete checklist
  - [x] Issue updated with status

## Rationale

This change corrects a systematic misalignment between GO and EC hierarchies that arose from the IUBMB's 2018 reclassification of most cytochrome P450 enzymes from EC 1.14.13 to EC 1.14.14. By ensuring GO parents match EC parents at the sub-subclass level, this improves ontology consistency and facilitates accurate cross-referencing between GO and EC classifications.

---
🤖 **Generated by claude agent**
- Runtime: `claude`
- Model: `claude-sonnet-4-5-20250929`
- Agent config: `ai4curation/go-ontology-agent-config@v9:.`
- Iteration: `1`
- Run: [View workflow run](https://github.com/ai4curation/eval-ont-agent-go/actions/runs/25847326548)
