# Fix Parentage Issues in Oxidoreductase Activity Branch

## Summary

This PR corrects 21 parentage and definition issues in the oxidoreductase activity branch of the Gene Ontology. All changes align enzymatic classification (EC) numbers with appropriate hierarchical parents in the GO term structure based on EC sub-subclass designations.

## Detailed Changes

### Reclassification Based on EC Sub-subclass

The core issue was that several terms were parented under GO terms corresponding to different EC sub-subclasses than their actual EC designations. The fixes reorganize the hierarchy to match:

#### Formate Dehydrogenases (EC 1.17 group)
- **GO:0008863** (formate DH NAD+, EC:1.17.1.9): Reparented from GO:0016620 (EC:1.2.1.-) to GO:0016726 (EC:1.17.1.-)
- **GO:0047899** (formate DH NADP+, EC:1.17.1.10): Reparented from GO:0016620 to GO:0016726
- **GO:0047111** (formate DH cytochrome, EC:1.17.2.3): Reparented from GO:0016622 to GO:0016725 (no specific GO term for EC:1.17.2.-)

Rationale: EC class 1.17 = "acting on CH or CH2 groups" ≠ 1.2 "acting on aldehyde or oxo group"

#### CH-NH Group Oxidoreductases
- **GO:0044684** (dihydromethanopterin reductase, EC:1.5.99.15): Reparented from GO:0016646 (EC:1.5.1.-) to GO:0016645 (EC:1.5.-.-); also updated definition
- Definition revised to reflect correct reversible reaction: "5,6,7,8-tetrahydromethanopterin + acceptor = 7,8-dihydromethanopterin + reduced acceptor"

Rationale: EC 1.5.99 (with unknown specific acceptor) ≠ 1.5.1 (NAD/NADP specific)

#### CH-CH Group Oxidoreductases
- **GO:0008762** (UDP-N-acetylmuramate dehydrogenase, EC:1.3.1.98): Reparented from GO:0016616 (EC:1.1.1.-) to GO:0016628 (EC:1.3.1.-)
- **GO:0008839** (4-hydroxy-THDP reductase, EC:1.17.1.8): Reparented from GO:0016628 to GO:0016726
- Definition updated with correct substrate names (alpha-D forms)

#### CH-OH Group Oxidoreductases  
- **GO:0050607** (S-(hydroxymethyl)mycothiol dehydrogenase, EC:1.1.1.306): Reparented from GO:0016620 to GO:0016616
- **GO:0018525** (4-hydroxybenzoyl-CoA reductase, EC:1.1.7.1): Reparented from GO:0016636 (EC:1.3.7.-) to GO:0016614
- **GO:0033717** (gluconate 2-dehydrogenase, EC:1.1.99.3): Reparented from GO:0008875 to GO:0016614

Rationale: EC 1.1.7 and 1.1.99 are CH-OH donors; placement under EC 1.3.x terms was incorrect

#### Monooxygenases vs Dioxygenases
- **GO:0010277** (chlorophyllide a oxygenase, EC:1.14.13.122): Reparented from GO:0016703 (dioxygenases) to GO:0016709 (monooxygenases with NAD(P)H)
- **GO:0050588** (apo-β-carotenoid dioxygenase, EC:1.13.11.67): Reparented from GO:0016703 (internal monooxygenase term) to GO:0016702 (dioxygenases)
- **GO:0102717** (DIBOA-glucoside oxygenase, EC:1.14.11.59): Reparented from GO:0050498 (EC:1.14.20.-) to GO:0016706 (EC:1.14.11.-)

Rationale: Enzymatic mechanism must match parent classification (internal vs paired donors)

#### 2-Oxoglutarate-Dependent Dioxygenases  
- **GO:0033759** (flavone synthase, EC:1.14.20.5)
- **GO:0045431** (flavonol synthase, EC:1.14.20.6)
- **GO:0047594** (6β-hydroxyhyoscyamine epoxidase, EC:1.14.20.13)
- **GO:0050589** (leucocyanidin oxygenase, EC:1.14.20.4)

All four reparented from GO:0016706 (EC:1.14.11.-) to GO:0050498 (EC:1.14.20.-)

Rationale: All are 2-OG dioxygenases but with EC:1.14.20 sub-subclass (cis-trans isomerase group)

#### Other Reclassifications
- **GO:0102394** (L-isoleucine 4-hydroxylase): Renamed from "dehydrogenase" (incorrect) and reparented to GO:0016706
- **GO:0047081** (3-hydroxy-2-methylpyridine-5-carboxylate monooxygenase): Renamed from "dioxygenase" form and reparented to GO:0016709
- **GO:0106145** (scopoletin 8-hydroxylase): Reparented from GO:0016709 to GO:0016706
- **GO:0050616** (secologanin synthase): Reparented from GO:0016634 to GO:0016717 (cytochrome P450)
- **GO:0102915** (piperitol synthase): Reparented from GO:0016709 to GO:0016717 (cytochrome P450)
- **GO:0032441** (pheophorbide a oxygenase): Reparented from GO:0016730 to GO:0016713 (iron-sulfur protein acceptor)
- **GO:0004498** & **GO:0036199** (vitamin D metabolism): Reparented from GO:0016709 to GO:0016713 (iron-sulfur protein acceptor)
- **GO:0018570** (p-cumate 2,3-dioxygenase): Reparented from GO:0016702 to GO:0016708

## Definitions Updated with RHEA References

Where applicable, definitions were updated to match RHEA (Rhea reactions) database entries and use the RHEA IDs as primary references:

- GO:0050607: RHEA:28502
- GO:0008762: RHEA:12248
- GO:0018525: Updated to reflect 4Fe-4S ferredoxin cofactor
- GO:0044684: RHEA:42804 (replacing GOC:mengo_curators)
- GO:0047081: Updated with correct reactants and products
- GO:0106145: Corrected formatting and spacing
- GO:0050616: Updated to reflect hemoprotein reductase cofactor
- GO:0102915: Updated with both main reaction and secondary activity
- GO:0032441: Updated to reflect 2Fe-2S ferredoxin specificity

## Validation

All changes maintain:
- Correct OBO syntax
- Appropriate parent-child relationships
- EC number alignment with hierarchy
- Reference integrity (PMID and RHEA)

## Work Process

1. Identified all 21 terms requiring fixes
2. Checked out terms using `obo-checkout.pl`
3. Made targeted edits to names, definitions, and parent relationships
4. Checked terms back in using `obo-checkin.pl`
5. Verified syntax and EC alignment
6. Committed with detailed message documenting each change

## Related Issues

This work addresses the comprehensive review from Claude AI4Curation that identified systematic misclassifications within the oxidoreductase activity branch of GO.

---
🤖 **Generated by claude agent**
- Runtime: `claude`
- Model: `claude-haiku-4-5-20251001`
- Agent config: `ai4curation/go-ontology-agent-config@v9:.`
- Iteration: `1`
- Run: [View workflow run](https://github.com/ai4curation/eval-ont-agent-go/actions/runs/25640389110)
