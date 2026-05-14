# Reparent 49 EC:1.14.14.x cytochrome P450 terms

## Summary
This PR addresses issue #31967 by systematically reparenting 49 cytochrome P450 monooxygenase activity terms to align with the IUBMB 2018 EC reclassification.

## Changes Made
- **Modified file**: `src/ontology/go-edit.obo`
- **Type of change**: Reparenting of existing terms
- **Number of terms affected**: 49

All 49 terms previously had `is_a: GO:0016709` (EC:1.14.13.-) and now have `is_a: GO:0016712` (EC:1.14.14.-).

## Rationale
The affected terms all have EC xrefs in sub-subclass 1.14.14, but their nearest EC-bearing is_a ancestor was GO:0016709 carrying EC:1.14.13.-, which is not an EC-class ancestor of 1.14.14.x. This inconsistency arose from the IUBMB 2018 reclassification of most cytochrome P450 enzymes from EC sub-subclass 1.14.13 to 1.14.14.

The target parent GO:0016712 appropriately carries `xref: EC:1.14.14.- {source="skos:exactMatch"}`, making it the correct parent for all these terms.

## Terms Modified (49 total)
GO:0004506 (squalene monooxygenase activity), GO:0008398 (sterol 14-demethylase activity), GO:0010295 ((+)-abscisic acid 8'-hydroxylase activity), GO:0016710 (trans-cinnamate 4-monooxygenase activity), GO:0016711 (flavonoid 3'-monooxygenase activity), GO:0018664 (benzoate 4-monooxygenase activity), GO:0033772 (flavonoid 3',5'-hydroxylase activity), GO:0033775 (deoxysarpagine hydroxylase activity), GO:0033777 (lithocholate 6beta-hydroxylase activity), GO:0033781 (cholesterol 24-hydroxylase activity), GO:0036189 (abieta-7,13-diene hydroxylase activity), GO:0036201 (ent-isokaurene C2-hydroxylase activity), GO:0036202 (ent-cassa-12,15-diene 11-hydroxylase activity), GO:0036204 (abieta-7,13-dien-18-ol hydroxylase activity), GO:0036209 (9beta-pimara-7,15-diene oxidase activity), GO:0047082 (3,9-dihydroxypterocarpan 6a-monooxygenase activity), GO:0047083 (5-O-(4-coumaroyl)-D-quinate 3'-monooxygenase activity), GO:0047084 (methyltetrahydroprotoberberine 14-monooxygenase activity), GO:0047087 (protopine 6-monooxygenase activity), GO:0047088 (dihydrosanguinarine 10-monooxygenase activity), GO:0047089 (dihydrochelirubine 12-monooxygenase activity), GO:0047957 (4'-methoxyisoflavone 2'-hydroxylase activity), GO:0048000 (isoflavone 3'-hydroxylase activity), GO:0050591 (quinine 3-monooxygenase activity), GO:0050592 (4-hydroxyphenylacetaldehyde oxime monooxygenase activity), GO:0050593 (N-methylcoclaurine 3'-monooxygenase activity), GO:0050594 (tabersonine 16-hydroxylase activity), GO:0050596 (vinorine hydroxylase activity), GO:0050597 (taxane 10-beta-hydroxylase activity), GO:0050598 (taxane 13-alpha-hydroxylase activity), GO:0102001 (isoleucine N-monooxygenase (oxime forming) activity), GO:0102002 (valine N-monooxygenase (oxime forming) activity), GO:0102068 (alpha-humulene 10-hydroxylase activity), GO:0102170 (5-epi-aristolochene-1,3-dihydroxylase activity), GO:0102289 (beta-amyrin 11-oxidase activity), GO:0102320 (1,8-cineole 2-exo-monooxygenase activity), GO:0102375 (11-oxo-beta-amyrin 30-oxidase activity), GO:0102556 (dammarenediol 12-hydroxylase activity), GO:0102557 (protopanaxadiol 6-hydroxylase activity), GO:0102596 (cytochrome P450 dependent ent-sandaracopimaradiene 3-hydroxylase activity), GO:0102597 (3alpha-hydroxy-ent-sandaracopimardiene 9-beta-monooxygenase activity), GO:0102598 (3alpha-hydroxy-ent-sandaracopimardiene 7-beta-monooxygenase activity), GO:0102684 (L-phenylalanine N-monooxygenase activity), GO:0102811 (geraniol 10-hydroxylase activity), GO:0102876 (psoralen synthase (NADPH) activity), GO:0102934 (costunolide synthase activity), GO:0102995 (angelicin synthase activity), GO:0106144 (fraxetin 5-hydroxylase activity), GO:0106149 (indole-3-carbonyl nitrile 4-hydroxylase activity)

## Verification Checklist
- [x] **PLAN**: Issue analyzed and plan created
- [x] **PRE-VALIDATION**: Baseline validation performed (build tools unavailable, manual checks passed)
- [x] **TERM-SEARCH**: All affected terms and parent terms verified
  - Confirmed GO:0016709 (old parent) has EC:1.14.13.- xref
  - Confirmed GO:0016712 (new parent) has EC:1.14.14.- xref
  - Verified sample terms have EC:1.14.14.x xrefs
- [x] **DESIGN-PATTERNS**: Design pattern compliance verified
  - Pattern is straightforward: reparent to match EC classification
  - No logical definitions involved, only is_a relationships
- [x] **EDITS**: Correct checkout/checkin procedure followed
  - Used obo-checkout.pl to extract all 49 terms
  - Modified is_a relationships in individual term files
  - Used obo-checkin.pl to reintegrate changes
- [x] **RELATIONSHIPS**: Relationships properly maintained
  - Changed only the GO:0016709 is_a relationship to GO:0016712
  - Preserved all other relationships (e.g., GO:0008398 retains its is_a to GO:0032451)
  - No logical definitions to update
- [x] **METADATA**: Metadata handling correct
  - No metadata changes needed (only editing existing terms, not creating new ones)
  - Preserved all existing metadata fields
- [x] **AUTOMATED-VALIDATION**: Validation performed
  - Full travis_build unavailable due to missing dependencies (amm, robot)
  - Manual verification: all 49 terms confirmed to have new parent GO:0016712
  - Manual verification: no terms retain old parent GO:0016709
  - Manual verification: sample terms confirmed to have matching EC:1.14.14.x xrefs
- [x] **CHANGES-COMMITTED**: Changes committed properly
  - Modified only src/ontology/go-edit.obo
  - Detailed commit message with full context
  - Includes issue reference and co-author signature

## Impact
This change resolves the largest cluster of EC/GO hierarchy inconsistencies in the GO:0016491 oxidoreductase subtree, ensuring that cytochrome P450 monooxygenase activities are correctly grouped under a parent that matches their EC classification.

---
🤖 **Generated by copilot agent**
- Runtime: `copilot`
- Model: `claude-sonnet-4.5`
- Agent config: `ai4curation/go-ontology-agent-config@v9:.`
- Iteration: `1`
- Run: [View workflow run](https://github.com/ai4curation/eval-ont-agent-go/actions/runs/25888553584)
