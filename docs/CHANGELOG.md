# NDA Analyzer - Changelog & Technical Reference

> Version history and technical specifications for the M&A NDA Analyzer

---

## Changelog

### v2.7 (Current) — Auto-Analyze Release

- **Auto-Analyze on Upload**: If user uploads NDA without specifying preferences, analyze immediately with defaults (no waiting)
- **matrix is TRUE default**: Risk Matrix only output, with "Want more detail?" options shown at end
- **OUTPUT_FORMAT hierarchy**:
  - `matrix` (DEFAULT): Risk Matrix tables only — quick risk overview
  - `summary`: Matrix + CRITICAL/HIGH findings
  - `full`: Matrix + All findings + Recommendations
  - `extended`: Full + Redline templates
  - `complete`: Extended + Legal sources + Cross-refs
- **SUGGEST_ADDITIONS parameter**: New parameter (default=Yes) that auto-generates:
  - Suggested text for missing clauses (e.g., PE Acknowledgement)
  - **Modified NDA Document**: Complete NDA with suggested clauses already inserted at appropriate locations, marked with `[ADDED]` tags
- **Format upsell**: matrix output now ends with "Want more detail?" offering other formats
- **Simplified parameters**: Removed `INCLUDE_REDLINES` and `GENERATE_PE_ACK` (now controlled by output format)
- **LITE now includes Legal Sources**: Case law references (Martin Marietta, Goodrich Capital v. Vector Capital) and Delaware statutes added to LITE versions
- All 4 prompt files updated (compressed/extended × FULL/LITE)

### v2.6.1 — Token Optimization Release

- **Created Standard (token-optimized) versions**:
  - `NDA_ANALYZER_PROMPT_FULL.md` reduced from 2107 to **444 lines (79% reduction)**
  - `NDA_ANALYZER_PROMPT_LITE.md` reduced from 275 to **131 lines (52% reduction)**
- **Created Extended versions** preserving full documentation:
  - `NDA_ANALYZER_PROMPT_FULL.md` (original FULL)
  - `NDA_ANALYZER_PROMPT_LITE.md` (original LITE)
- Standard versions maintain **full semantic power** — same 26 clauses, same analysis rules
- Extended versions include: negotiation positions, usage examples, detailed explanations
- Reorganized folder structure: `prompts/compressed/`, `prompts/extended/`, `docs/`

### v2.6

- Added **TRANSACTION_TYPE parameter** (M&A/JV/Strategic Partnership/Licensing/Minority Investment/Due Diligence Only) with automatic severity adjustment for non-M&A contexts
- Added **OUTPUT FORMAT DISCIPLINE** - explicit rules for what each format (Executive/Summary/Full) includes and excludes
- Added **ANTI-NOISE RULES** - Flag Justification Threshold and Executive Prioritization (max 5 issues + 5 recommendations)
- Added **TOKEN EFFICIENCY** - cross-reference legal doctrines instead of repeating explanations
- Added **EXECUTIVE LANGUAGE GUIDE** - legal-to-business translation table for summaries
- Added **ASSUMPTIONS APPLIED** disclosure block at report start
- Added **Analysis Engine** version traceability in report footer
- Enhanced **CONFIDENCE LEVELS** with specific phrases ("High confidence under Delaware precedent", etc.)
- Added **LEGAL SOURCES REFERENCE** - per-clause source mapping with case law citations, Delaware statutory references
- Total clauses unchanged: **26** (operational enhancements only)

### v2.5

- Added **Generative AI / Cloud Restrictions** as new Tier 2 clause (#16) - analyzes LLM, ChatGPT, and cloud service restrictions
- Added **No Representations / Accuracy of Information** as new Tier 3 clause (#26) - analyzes accuracy disclaimers and fraud carve-outs
- Added **AI Readiness Assessment** to Executive Summary (High / Low / Silent)
- Enhanced **Defined Terms Summary** with Trade Secrets and Permitted Representatives entries
- Updated **Keywords table** with AI and accuracy-related terms
- Renumbered Tier 3 clauses (#17-26)
- Total clauses now: **26** (Tier 1: 9, Tier 2: 7, Tier 3: 10)

### v2.4

- Added **Quick Analysis Checklist** - Complete checklist for ensuring analysis coverage
- Added **Cross-Reference Checks** section with 7 mandatory clause interaction checks
- Added **Severity Calibration Guide** for consistent CRITICAL/HIGH/MEDIUM/LOW classification
- Added **Deal Context Factors** - Adjust analysis based on deal type
- Added **Common Drafting Errors** detection (circular definitions, orphaned references, etc.)
- Added **Signature Block Review** to Preliminary Checks
- Added **Equitable Relief / Irreparable Harm** as new Tier 3 clause (#24)
- Added **Alternative Structures Check** to Use Clause (tender offer, proxy, club deal, etc.)
- Added **REASONING STEPS** to Non-Solicitation (#4) and Return of Information (#6)
- Added **NOT PRESENT Finding Template** for standardized missing clause documentation
- Added **Analysis Parameters Applied** to output header
- Added **Execution Status** to output header
- Updated **Administrative Provisions** to clause #25

### v2.3

- **LITE Version Created** - New streamlined prompt with only 6 client-requested core clauses
- Added **Preliminary Checks** section (NDA type detection, defined terms inventory, document quality)
- Added **Quote-Before-Assess Rule** to Critical Operating Rules
- Added **Critical Analytical Constraints** to System Instructions
- Added **REASONING STEPS** (Chain-of-Thought) to Use Clause (#3), PE Acknowledgement (#7), Representative Liability (#9)
- Added **Warning Labels** to Break-up Fee (#10), Standstill (#11), Residuals (#16)
- Added **Handling Ambiguity** section with Confidence Levels (HIGH/MEDIUM/LOW)
- Added **Administrative Provisions Quick Check** (#23)
- Added **Common Negotiation Positions** section with ready-to-use talking points
- Added **Defined Terms Summary** to output format
- Added **Document Type** (One-Way/Mutual/Hybrid) to output header

### v2.2

- Added **Privacy & Data Integrity Guardrails** (no-training rule, PII awareness)
- Added **Representative Liability** as new Tier 1 clause (#9)
- Added **Compelled Disclosure Protocol** to Tier 2 (#13)
- Added **Integration/Supersession** check to Tier 2 (#14)
- Added **Jurisdictional Conflict Analysis** to Non-Delaware Impact Assessment
- Enhanced **Residuals** with Trade Secret/Patent exclusion check
- Added **Data Privacy/PII Compliance** row to Executive Summary
- Added **Inter-Agreement Risks** row to Executive Summary

### v2.1

- Added **Anti-Hallucination Guardrails** (NOT PRESENT requirement)
- Added **Use Clause / Purpose Limitation** as core clause
- Added **Affiliate & Portfolio Company Definition** analysis
- Added **Delaware Baseline** enforcement (non-Delaware flagging)
- Added **Non-Delaware Governing Law Impact Assessment** section
- Added **Strictness behavioral definitions**
- Added **Transaction Definition** check ("between" vs "involving")
- Expanded **Residual Clause** handling
- Added **Use Clause redline template**

### v2.0

- Added configurable parameters
- Added Seller perspective
- Added PE Acknowledgement generator
- Added Redline templates

### v1.0

- Initial release (Buyer perspective only)

---

## Clauses Analyzed

### Tier 1: Core Clauses (9 clauses)

| # | Clause | Description |
|---|--------|-------------|
| 1 | Governing Law (Delaware Baseline) | Jurisdiction and applicable law |
| 2 | Term / Duration | Agreement duration and expiration |
| 3 | Use of Confidential Information | Purpose limitations and "Transaction" definitions |
| 4 | Non-Solicitation of Employees | Hiring restrictions with exceptions |
| 5 | Non-Circumvention | Direct contact and fee protection clauses |
| 6 | Return of Confidential Information | Destruction/retention requirements |
| 7 | PE Acknowledgement | Private equity business acknowledgement |
| 8 | Affiliate & Portfolio Company Definition | Scope of affiliated entities |
| 9 | Representative Liability | Vicarious liability for advisors/agents |

### Tier 2: High-Risk Clauses (7 clauses)

| # | Clause | Description |
|---|--------|-------------|
| 10 | Break-up Fee / Termination Fee | Payment obligations on deal termination |
| 11 | Standstill Provisions | Acquisition activity restrictions |
| 12 | Financing Source Restrictions | Limitations on financing communications |
| 13 | Liquidated Damages | Predetermined breach penalties |
| 14 | Compelled Disclosure Protocol | Legal process disclosure requirements |
| 15 | Integration / Supersession | Impact on prior agreements |
| 16 | Generative AI / Cloud Restrictions | AI tool and cloud service limitations |

### Tier 3: Medium-Risk Clauses (10 clauses)

| # | Clause | Description |
|---|--------|-------------|
| 17 | Residual Clauses | Unaided memory provisions |
| 18 | Exclusivity / No-Shop | Negotiation exclusivity |
| 19 | Perpetual Obligations | Indefinite term provisions |
| 20 | Jury Trial Waiver | Jury right waiver |
| 21 | Broad Definition of CI | Confidential information scope |
| 22 | Forum Selection | Exclusive jurisdiction clauses |
| 23 | Damages Waiver | Consequential damages limitations |
| 24 | Equitable Relief / Irreparable Harm | Injunctive relief stipulations |
| 25 | Administrative Provisions | Assignment, Amendment, Notices, Counterparts |
| 26 | No Representations / Accuracy | Information accuracy disclaimers |

### Cross-Reference Checks (7 mandatory)

1. Use Clause ↔ Standstill (backdoor standstill risk)
2. PE Ack ↔ Affiliate Definition (protection consistency)
3. Rep Liability ↔ Representatives Definition (scope match)
4. Term ↔ Perpetual Obligations (survival consistency)
5. Return of Info ↔ Retention Rights (no conflicts)
6. Compelled Disclosure ↔ Return of Info (retained copy disclosure)
7. Assignment ↔ Financing Sources (PE consistency)

---

## Understanding the Output

### Risk Levels

| Level | Meaning | Action |
|-------|---------|--------|
| **CRITICAL** | Deal-breaker potential | Must address before signing |
| **HIGH** | Significant risk | Should negotiate |
| **MEDIUM** | Notable issue | Consider negotiating |
| **LOW** | Minor concern | Acceptable, note for awareness |

### Status Indicators

| Status | Meaning |
|--------|---------|
| **OK** | Clause meets acceptable criteria |
| **FLAG** | Clause requires attention |
| **NOT PRESENT** | Clause not found in NDA |

### Classifications

| Term | Meaning |
|------|---------|
| **Buyer-Friendly** | Favors the potential acquirer |
| **Seller-Friendly** | Favors the target company |
| **Market Standard** | Common/neutral language |
| **Balanced** | Fair to both parties |

### Output Fields

| Field | Values | Location |
|-------|--------|----------|
| Execution Status | Executed / DRAFT - NOT EXECUTED | Header |
| Analysis Parameters Applied | Perspective, Strictness, Transaction Type, PE Mode, Deal Context | Header |
| Assumptions Applied | Standardized disclaimer block | Header |
| Document Type | One-Way / Mutual / Hybrid | Header |
| Defined Terms Summary | List of key defined terms | After Header |
| Data Privacy/PII Compliance | Compliant / High Risk / Not Mentioned | Executive Summary |
| Inter-Agreement Risks | Yes / No | Executive Summary |
| AI Readiness | High / Low / Silent | Executive Summary |
| Confidence Level | HIGH / MEDIUM / LOW + phrase | Per-clause findings |
| Analysis Engine | Base Prompt version, parameters used | Report Footer |

### Output Sections

| Section | Purpose |
|---------|---------|
| NOT PRESENT FINDING TEMPLATE | Standardized format for missing clauses |
| QUICK ANALYSIS CHECKLIST | Ensures analysis completeness |
| DEFINED TERMS SUMMARY | Inventories key terms |
| COMMON NEGOTIATION POSITIONS | Ready-to-use talking points |
| DATA PRIVACY / PII COMPLIANCE | GDPR/CCPA implications |
| INTER-AGREEMENT RISKS | Prior agreement impact |

---

## Anti-Hallucination Feature

The prompt includes guardrails to prevent the LLM from assuming clauses exist.

**What you'll see:**
```
Non-Circumvention: NOT PRESENT in this NDA
PE Acknowledgement: NOT PRESENT - recommend adding
Standstill: NOT PRESENT
```

**What you won't see (prevented):**
```
Non-Circumvention: Not explicitly stated but likely covered under...
PE Acknowledgement: Standard provisions would typically include...
```

**If the LLM starts assuming, remind it:**
```
Remember: Only report clauses that are actually present. Mark missing clauses as "NOT PRESENT".
```

---

## Files Reference

### Prompt Files

| Location | File | Lines | Purpose |
|----------|------|-------|---------|
| `prompts/compressed/` | `NDA_ANALYZER_PROMPT_FULL.md` | ~444 | Standard FULL - 26 clauses, token-optimized |
| `prompts/compressed/` | `NDA_ANALYZER_PROMPT_LITE.md` | ~131 | Standard LITE - 6 core clauses |
| `prompts/extended/` | `NDA_ANALYZER_PROMPT_FULL.md` | ~2107 | Extended FULL - full documentation |
| `prompts/extended/` | `NDA_ANALYZER_PROMPT_LITE.md` | ~275 | Extended LITE - detailed explanations |

### Comparison: Standard vs Extended

| Aspect | Standard | Extended |
|--------|----------|----------|
| All 26 clauses | Yes | Yes |
| Core analysis rules | Yes | Yes |
| Severity guide | Yes | Yes |
| Output format | Yes | Yes |
| Redline templates | Yes | Yes |
| Legal sources | Yes | Yes |
| Negotiation positions | No | Yes |
| Usage examples | No | Yes |
| Detailed explanations | Condensed | Full |

---

## Key Legal Cases Referenced

| Case | Year | Relevance |
|------|------|-----------|
| *Martin Marietta v. Vulcan Materials* | 2012 | "Use" clauses can operate as de facto standstill |
| *Space Data Corp. v. Google* | 2017 | Residual clauses make proving breach difficult (NOT Delaware - persuasive only) |
| *Goodrich Capital v. Vector Capital* | 2012 | Non-circumvention can create $3.5M+ liability (S.D.N.Y.) |

---

*Version 2.7 | January 2026 | Auto-Analyze Release*
