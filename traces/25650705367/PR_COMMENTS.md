## Summary

Addresses issue #31969 — parentage problems in the oxidoreductase activity branch. Twenty-five MF terms had `is_a` parents whose EC sub-subclass did not match the term's own EC sub-subclass, and a subset needed RHEA-aligned definition rewrites and/or name corrections.

All edits performed via `obo-checkout.pl` → file edits in `terms/` → `obo-checkin.pl` against `src/ontology/go-edit.obo`. A `term_tracker_item` pointing to issue #31969 was added to every modified term.

## Changes by term

### Reparent only

| Term | Old parent | New parent | Rationale |
|---|---|---|---|
| GO:0008863 (formate DH (NAD+), EC:1.17.1.9) | GO:0016620 (EC:1.2.1.-) | GO:0016726 (EC:1.17.1.-) | EC class 1.17 ≠ 1.2 |
| GO:0047899 (formate DH (NADP+), EC:1.17.1.10) | GO:0016620 (EC:1.2.1.-) | GO:0016726 (EC:1.17.1.-) | Same as above |
| GO:0047111 (formate DH (cyt-c-553), EC:1.17.2.3) | GO:0016622 (EC:1.2.2.-) | GO:0016725 (EC:1.17.-.-) | No GO class for EC:1.17.2.-; parent on class only |
| GO:0008839 (4-OH-THDP reductase, EC:1.17.1.8) | GO:0016628 (EC:1.3.1.-) | GO:0016726 (EC:1.17.1.-) | EC class 1.17 ≠ 1.3 |
| GO:0033717 (gluconate 2-DH (acceptor), EC:1.1.99.3) | GO:0008875 (a NAD/NADP child of GO:0016616) | GO:0016614 (EC:1.1.-.-) | EC sub-subclass .99 ≠ .1 |
| GO:0010277 (chlorophyllide a oxygenase, EC:1.14.13.122) | GO:0016703 (EC:1.13.12.-) | GO:0016709 (EC:1.14.13.-) | Wrong class; not an internal monooxygenase |
| GO:0050588 (apo-β-carotenoid 14',13'-dioxygenase, EC:1.13.11.67) | GO:0016703 (EC:1.13.12.-, internal monooxygenase) | GO:0016702 (EC:1.13.11.-) | Dioxygenase, not monooxygenase |
| GO:0033759 (flavone synthase, EC:1.14.20.5) | GO:0016706 (EC:1.14.11.-) | GO:0050498 (EC:1.14.20.-) | EC sub-subclass mismatch |
| GO:0045431 (flavonol synthase, EC:1.14.20.6) | GO:0016706 | GO:0050498 | Same |
| GO:0047594 (6β-hydroxyhyoscyamine epoxidase, EC:1.14.20.13) | GO:0016706 | GO:0050498 | Same |
| GO:0050589 (leucocyanidin oxygenase, EC:1.14.20.4) | GO:0016706 | GO:0050498 | Same |
| GO:0004498 (calcidiol 1-monooxygenase, EC:1.14.15.18) | GO:0016709 (EC:1.14.13.-) | GO:0016713 (EC:1.14.15.-) | Sub-subclass mismatch |
| GO:0036199 (cholest-4-en-3-one 26-monooxygenase, EC:1.14.15.29) | GO:0016709 | GO:0016713 | Same |
| GO:0018570 (p-cumate 2,3-dioxygenase, EC:1.14.12.25) | GO:0016702 (EC:1.13.11.-) | GO:0016708 (EC:1.14.12.-) | EC sub-subclass mismatch |

### Reparent + def rewrite

| Term | Old parent | New parent | Def change |
|---|---|---|---|
| GO:0050607 (renamed → "S-(hydroxymethyl)mycothiol dehydrogenase activity"; old name as RELATED synonym) | GO:0016620 (EC:1.2.1.-) | GO:0016616 (EC:1.1.1.-) | Now reads `S-(hydroxymethyl)mycothiol + NAD+ = S-formylmycothiol + NADH + H+` per RHEA:28502 |
| GO:0008762 (UDP-N-acetylmuramate DH, EC:1.3.1.98) | GO:0016616 (EC:1.1.1.-) | GO:0016628 (EC:1.3.1.-) | Substrate/product α-stereochem clarified per RHEA:12248 |
| GO:0018525 (4-hydroxybenzoyl-CoA reductase, EC:1.1.7.1) | GO:0016636 (EC:1.3.7.-) | GO:0016614 (EC:1.1.-.-) | Def updated to RHEA:29603 form with `2[4Fe-4S]-[ferredoxin]` |
| GO:0044684 (dihydromethanopterin reductase, EC:1.5.99.15) | GO:0016646 (EC:1.5.1.-) | GO:0016645 (EC:1.5.-.-) | Def now matches RHEA:42804 (`+ acceptor`/`+ reduced acceptor`); replaced `GOC:mengo_curators` xref with `RHEA:42804`, kept PMID:15028691 |
| GO:0047081 (renamed → "3-hydroxy-2-methylpyridine-5-carboxylate monooxygenase [NAD(P)H] activity"; old name as RELATED synonym) | GO:0016708 (EC:1.14.12.-) | GO:0016709 (EC:1.14.13.-) | Def reordered per issue text |
| GO:0106145 (scopoletin 8-hydroxylase, EC:1.14.11.60) | GO:0016709 (EC:1.14.13.-) | GO:0016706 (EC:1.14.11.-) | Def fixed (typo `Catalyzes`, missing spaces/equals); xrefs preserved |
| GO:0102717 (DIBOA-glucoside oxygenase, EC:1.14.11.59) | GO:0050498 (EC:1.14.20.-) | GO:0016706 (EC:1.14.11.-) | Def updated to RHEA:32115 wording; def xref reduced to RHEA:32115 |
| GO:0050616 (secologanin synthase, EC:1.14.19.62) | GO:0016634 (EC:1.3.3.-) | GO:0016717 (EC:1.14.19.-) | Def updated to RHEA:20585 wording (P450 reductase form); def xref reduced to RHEA:20585 |
| GO:0102915 (piperitol synthase, EC:1.14.19.74) | GO:0016709 (EC:1.14.13.-) | GO:0016717 (EC:1.14.19.-) | Def updated to the issue-supplied wording including the (+)-sesamin side note; PMID:16785429 retained as def xref |
| GO:0032441 (pheophorbide a oxygenase, EC:1.14.15.17) | GO:0016730 (EC:1.18.-.-) | GO:0016713 (EC:1.14.15.-) | Def updated to RHEA:48140 wording; RHEA:48140 added as def xref |

### Rename + reparent (no def change)

| Term | Action |
|---|---|
| GO:0102394 | Renamed "4-hydroxy-L-isoleucine dehydrogenase activity" → "L-isoleucine 4-hydroxylase activity" (the previous label was a misnomer for EC:1.14.11.45, which is a 2-OG-dependent dioxygenase). Old name kept as RELATED synonym. Reparented from GO:0016616 (EC:1.1.1.-) to GO:0016706 (EC:1.14.11.-). |

## Checklist

- [x] PLAN — issue reviewed in full; all 25 sub-items addressed
- [x] PRE-VALIDATION — current ontology parsed; basic structure intact (~48,306 stanzas). Full ROBOT/ELK build not available in this environment
- [x] RESEARCH — N/A; issue body itself supplied the reasoning and target reactions/parents (cross-checked against EC and RHEA mappings already present on the terms)
- [x] TERM-SEARCH — all old/new parents and child terms verified to exist via `obo-grep.pl`
- [x] DESIGN-PATTERNS — N/A; no new compositional logical definitions introduced. All edits operate on existing `is_a` assertions and text definitions; no `intersection_of` axioms added
- [x] EDITS — `obo-checkout.pl`/`obo-checkin.pl` workflow used; `terms/` cleared
- [x] RELATIONSHIPS — each modified term retains exactly one asserted `is_a` parent; no over-assertion
- [x] METADATA — no `created_by`/`creation_date` added (all terms pre-existing); a `term_tracker_item` for issue #31969 added to every modified term
- [ ] AUTOMATED-VALIDATION — `make travis_build` not runnable here (no `robot` binary). **Reviewer should re-run in CI.** No structural change that would alter reasoning beyond `is_a` swaps within sibling oxidoreductase classes — no unsat expected
- [x] REFERENCE-VALIDATION — all RHEA/PMID xrefs were already present on the corresponding terms; no new external references invented
- [x] CHANGES-COMMITTED — single commit on `src/ontology/go-edit.obo` only

## Notes / open questions

- For terms reparented away from a more-specific parent (e.g. GO:0033717 leaving GO:0008875, GO:0018525 leaving GO:0016636), I kept only the new asserted parent and did not add a secondary `is_a` to a more-specific descendant — matching the issue text. If a reviewer wants any of these to retain additional relations (e.g. an `acceptor` relation to capture the cytochrome/iron-sulfur acceptor link that's no longer in the parent chain), happy to add them; the issue didn't request that and the EC `.99`/`.-.-` classes are exactly the "generic acceptor" cases, so I left them as is.
- One def quirk I noticed but did not touch (out of scope): the existing text def for GO:0008839 writes the reaction in the reductase-product-on-the-left direction, which mismatches the EC narrative; the parent fix doesn't change that.

---
🤖 **Generated by claude agent**
- Runtime: `claude`
- Model: `claude-opus-4-7`
- Agent config: `ai4curation/go-ontology-agent-config@v9:.`
- Iteration: `1`
- Run: [View workflow run](https://github.com/ai4curation/eval-ont-agent-go/actions/runs/25650705367)
