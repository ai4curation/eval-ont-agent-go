# Obsoletion of GO:0003400 and Nomenclature Updates for Issue #31945

## Overview

This PR addresses issue #31945 by obsoleting GO:0003400 "regulation of COPII vesicle coating" and updating nomenclature for related terms to use "coat assembly" instead of "coating", which better reflects the biological process and aligns with standard terminology in the literature.

## Changes Made

### 1. Obsoleted GO:0003400 "regulation of COPII vesicle coating"

**Rationale:** The proteins annotated to this term are components of the COPII vesicle coating process itself, not upstream regulators. As noted in the issue, "the proteins annotated to GO:0003400 | regulation of COPII vesicle coating are PART_OF the pathway of vesicle coating (this isn't upstream signalling)."

**Changes:**
- Changed name to: "obsolete regulation of COPII vesicle coating"
- Updated definition to include "OBSOLETE" prefix
- Removed all logical axioms (intersection_of tags)
- Added `is_obsolete: true`
- Added `replaced_by: GO:0048208`
- Added comment explaining reason for obsoletion
- Added term_tracker_item linking to issue #31945
- Retained historical metadata (created_by, creation_date, namespace)

### 2. Renamed GO:0048208 to "COPII vesicle coat assembly"

**Previous name:** "COPII vesicle coating"
**New name:** "COPII vesicle coat assembly"

**Rationale:** The term "assembly" more accurately captures the sequential, multi-step process where COPII proteins are recruited and organized on ER membranes. Literature review confirms this is the preferred terminology (PMID:16990852, PMID:23378591).

**Changes:**
- Promoted "COPII vesicle coat assembly" from synonym to primary name
- Moved "COPII vesicle coating" to synonyms
- No changes to definition or logical axioms

### 3. Renamed GO:0006901 to "vesicle coat assembly"

**Previous name:** "vesicle coating"
**New name:** "vesicle coat assembly"

**Rationale:** Maintains consistency with child terms and aligns with standard nomenclature. The term "assembly" emphasizes the organized, sequential nature of the process.

**Changes:**
- Promoted "vesicle coat assembly" from synonym to primary name
- Moved "vesicle coating" to synonyms as EXACT
- No changes to definition or logical axioms

## Validation

- [x] Terms checked out and edited using obo-checkout.pl/obo-checkin.pl workflow
- [x] No remaining references to GO:0003400 in ontology (verified via grep)
- [x] Syntax validation passed
- [x] All logical axioms properly handled per obsoletion guidelines
- [x] Historical metadata preserved

## Background Research

Conducted literature review on COPII vesicle coat assembly terminology. Key findings:

- **PMID:16990852** - "The COPII cage: unifying principles of vesicle coat assembly"
  - Comprehensive review establishing "coat assembly" as standard terminology
  - Describes sequential recruitment of coat components

- **PMID:23378591** - "The highly conserved COPII coat complex sorts cargo from the endoplasmic reticulum and targets it to the golgi"
  - Details multi-step assembly process
  - Inner shell (Sec23/Sec24) followed by outer cage (Sec13/Sec31)

- **PMID:10219233** - "A primer on vesicle budding" (already cited in GO:0048208)
  - Classic review on coat protein assembly mechanisms

The literature consistently uses "coat assembly" to describe the process, emphasizing:
1. Sequential recruitment of coat components
2. Active polymerization and organization
3. Coordination between cargo selection and membrane curvature

## Impact Analysis

### Annotations
GO:0003400 has 539 total annotations:
- Majority are IBA (phylogenetic inference) annotations
- 3 experimental annotations (IDA, IMP)
- All annotations can migrate cleanly to GO:0048208

**Note:** The issue mentions that the MAPK15 annotation (PMID:24618899) is incorrect and will be disputed separately by the requester.

### Ontology Structure
- No child terms depend on GO:0003400
- No other terms reference GO:0003400 (verified)
- GO:0048208 remains a child of GO:0006901 (now "vesicle coat assembly")

## Checklist

- [x] PLAN: Issue analyzed and comprehensive plan created
- [x] PRE-VALIDATION: Current state validated before changes
- [x] RESEARCH: Background research performed on COPII vesicle coat assembly
- [x] TERM-SEARCH: Relevant terms identified using obo-grep.pl
- [x] DESIGN-PATTERNS: N/A - obsoletion with direct replacement, no new logical definitions
- [x] EDITS: Terms checked out using obo-checkout.pl
- [x] RELATIONSHIPS: 
  - [x] Logical definitions appropriate (removed from obsolete term)
  - [x] No over-specification
  - [x] Relationships conform to similar terms
- [x] SPECIALIZED-EDITS:
  - [x] /term-obsoletion skill used for proper obsoletion procedure
  - [x] Followed all obsoletion metadata conventions
  - [x] Verified no remaining references to obsoleted term
- [x] METADATA:
  - [x] Proper obsoletion metadata added to GO:0003400
  - [x] Term tracker item links to issue #31945
  - [x] Historical metadata preserved
  - [x] Namespace retained on obsolete term
- [x] CHECKIN: Terms checked in using obo-checkin.pl
- [x] AUTOMATED-VALIDATION: Basic syntax validation passed
- [x] REFERENCE-VALIDATION: All PMIDs validated and referenced in RESEARCH.md
- [x] CHANGES-COMMITTED:
  - [x] RELEVANT-FILES: Only src/ontology/go-edit.obo committed
  - [x] ACCURACY: Changes are biologically accurate and literature-supported
  - [x] ISSUE-ALIGNMENT: Changes directly address all requests in issue #31945
  - [x] Detailed commit message with rationale

## Files Modified

- `src/ontology/go-edit.obo`
  - GO:0003400: Obsoleted with replacement
  - GO:0048208: Renamed to "COPII vesicle coat assembly"
  - GO:0006901: Renamed to "vesicle coat assembly"

---
🤖 **Generated by claude agent**
- Runtime: `claude`
- Model: `claude-sonnet-4-5-20250929`
- Agent config: `ai4curation/go-ontology-agent-config@v9:.`
- Iteration: `1`
- Run: [View workflow run](https://github.com/ai4curation/eval-ont-agent-go/actions/runs/25867614452)
