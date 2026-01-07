# NDA Analyzer - Client Requirements (Original Text Only)

> This document contains ONLY information extracted from the text provided by the client. No interpretations or additional suggestions.

---

## 1. Client Context

- **Type**: Small Independent Sponsor firm (Halmos Capital)
- **Portfolio**: Few portcos
- **Team**: Small, looking for efficiencies
- **Requested Projects**: NDA Analyzer + SIM Analyzer (separate)

---

## 2. NDA Analyzer Strategic Vision

> "We should keep this simple or even build a freebie we can use as a door opener"

> "I really kinda like the NDA analyzer as a door opener REEA could offer others because its simple-ish but solves a problem that gives us a chance to get people on the platform"

> "Maybe its a small monthly fee but on the platform?"

**Client Conclusion**: Simple tool, possibly free or with a low monthly fee, to attract users to the REEA platform.

---

## 3. Andrew's General Use Cases

Andrew identified three areas for AI application:

| Area | Description |
|------|-------------|
| **Operations** | Automate low-value admin tasks (e.g., SEC filings, bill pay) |
| **Business Development** | Monitor emails from part-time BD person to ensure timely responses |
| **Investment Process** | Automate high-volume, repetitive tasks to reduce dependence on individuals |

### Specific tasks mentioned for automation:
- NDA review
- SIM analysis & summary
- Drafting IOIs & LOIs
- Creating pitch decks

---

## 4. NDA Analyzer Specific Requirements

### 4.1 Clauses to Analyze

> **Terminology**: Standard M&A nomenclature is used: **Buyer-Friendly** (favors the buyer), **Seller-Friendly** (favors the seller), **Market Standard** (neutral/common in the market), **Balanced** (equitable).

| # | Clause | Client's Exact Criteria | Impact |
|---|--------|-------------------------|--------|
| 1 | **Governing Law** | "State of Delaware" | **Market Standard** - Delaware benefits both parties (predictability, Court of Chancery) |
| 2 | **Term** | "2 Years (or less)" | **Buyer-Friendly** if ≤2 years. Long term is Seller-Friendly |
| 3 | **Non-Solicit** | "Solicitation through the use of general advertisements and employment agencies not directed specifically to any such officers, directors or employees is permitted. Anything else should be flagged" | **Buyer-Friendly** if has exceptions. Without exceptions is Seller-Friendly |
| 4 | **Non-Circumvention** | "This should be flagged if it exists" | **Seller-Friendly** - Creates liability for the buyer. Protects broker/seller fees |
| 5 | **Return of Confidential Information** | "Retain at least one copy of Confidential Information excluding copies required for internal archival procedures" | **Buyer-Friendly** if allows retention. Without retention is Seller-Friendly |
| 6 | **Private Equity Acknowledgement** | See full text below - "we would like to try and add this into the NDA's when possible. Would be great to create a widget to do that" | **Buyer-Friendly** - Protects PE buyer from restrictions on portfolio companies |

### 4.2 Full Text - Private Equity Acknowledgement

```
The Company acknowledges that (i) you and your affiliates are engaged in the
business of private equity investing and may from time to time invest in entities
that develop and utilize technologies, products or services that are similar to
or competitive with those of the Company, and (ii) except insofar as this
Agreement restricts the disclosure of the Evaluation Material, this Agreement
shall not prevent you or your affiliates from (a) engaging in or operating any
business, (b) entering into any agreement or business relationship with any
third party, or (c) evaluating or engaging in investment discussions with, or
investing in, any third party, whether or not competitive with the Company or
its affiliates. The Company acknowledges that your or your affiliates' directors,
officers or employees may serve as directors of portfolio companies of investment
funds managed by you, and the Company agrees that such portfolio companies will
not be deemed to have received Evaluation Material solely because any such
individual serves on the board of such portfolio company; provided, that (i)
such individual has not provided such portfolio company or any other director,
officer, employee or other representative of such portfolio company with
Evaluation Material unless in the context of a potential transaction with that
respective portfolio company and (ii) such portfolio company does not act at
the direction of or with encouragement from you.
```

### 4.3 Anomaly Detection

> "if it can somehow access the web / ChatGPT / etc and flag anything that looks truly abnormal for an NDA that would also be helpful"

> "For example, if someone hid something in there where we agreed to pay them a break up fee or something that would be highly unusual and we'd want the scanner to flag it"

> "ChatGPT has done a good job of this"

---

## 5. Materials Provided by Client

### 5.1 Materials Status

| Material | Status |
|----------|--------|
| Sample NDA (form NDA) | **RECEIVED** - "Project Toro - Form of Non-Disclosure Agreement" |
| Key terms for analysis | **RECEIVED** - The 6 clauses documented above |
| Examples of approved NDAs | **RECEIVED** - 9 NDAs in `/sample-ndas/` folder |
| Investment thesis (for SIM analyzer) | Pending delivery |

### 5.2 NDA Library Received (9 documents)

| # | File | Project | Type |
|---|------|---------|------|
| 1 | `Project Ampere - Confidentiality Agreement_vF (Edits).docx` | Ampere | Standard M&A NDA |
| 2 | `Project Toro - Form of Non-Disclosure Agreement (1).docx` | Toro | **Halmos Form NDA** |
| 3 | `NDA - Buyer & Seller Intro & CA (Halmos Redline) (1).docx` | N/A | Broker NDA (different) |
| 4 | `Project REMBRANDT - NDA - Halmos Capital (1).docx` | Rembrandt | Standard M&A NDA |
| 5 | `Project Crimson - Confidentiality Agreement (NDA)_Halmos Capital (1).docx` | Crimson | Standard M&A NDA |
| 6 | `Project Platform - NDA (1).DOCX` | Platform | Standard M&A NDA |
| 7 | `Project Viking - NDA (Halmos Redline) (1).docx` | Viking | M&A NDA with redlines |
| 8 | `Project Discovery NDA (1).docx` | Discovery | M&A NDA with PE Ack |
| 9 | `Project Flash - Prospective Buyer NDA (1).docx` | Flash | Standard M&A NDA |

---

## 6. Sample NDA Analysis - Criteria Validation

### 6.1 Governing Law (Delaware)

| NDA | Governing Law | Status |
|-----|---------------|--------|
| Ampere | Delaware | OK |
| Toro | Delaware | OK |
| Buyer & Seller | Delaware | OK |
| Rembrandt | Delaware | OK |
| Crimson | Delaware | OK |
| Platform | Delaware | OK |
| Viking | Delaware | OK |
| Discovery | Delaware | OK |
| Flash | Delaware | OK |

**Result**: 100% consistency - All use Delaware

### 6.2 Term (2 years or less)

| NDA | Term | Status |
|-----|------|--------|
| Ampere | 2 years | OK |
| Toro | 2 years | OK |
| Buyer & Seller | 2 years | OK |
| Rembrandt | 2 years | OK |
| Crimson | 2 years | OK |
| Platform | 2 years | OK |
| Viking | 2 years | OK |
| Discovery | 2 years | OK |
| Flash | 2 years | OK |

**Result**: 100% consistency - All are 2 years

### 6.3 Non-Solicit (Allow general advertisements)

| NDA | Allows general solicitation | Status |
|-----|------------------------------|--------|
| Ampere | Yes - "general public advertisements or search firms" | OK |
| Toro | Yes - "general job advertisements... recruiting firm" | OK |
| Buyer & Seller | Yes - "general job advertisement or recruiting agency" | OK |
| Rembrandt | Yes - "general solicitations... advertisements" | OK |
| Crimson | Yes - "general solicitation... advertisement" | OK |
| Platform | Yes - "general public employment solicitation" | OK |
| Viking | Yes - "general solicitation... general advertisements" | OK |
| Discovery | Yes - "generalized solicitation... advertisements" | OK |
| Flash | Yes - "general solicitation for employment" | OK |

**Result**: 100% consistency - All allow general solicitation

### 6.4 Non-Circumvention (FLAG if exists)

| NDA | Has Non-Circumvention | Status |
|-----|-------------------------|--------|
| Ampere | NO | OK |
| Toro | NO | OK |
| **Buyer & Seller** | **YES - Explicit Section 4** | **FLAG** |
| Rembrandt | NO | OK |
| Crimson | NO | OK |
| Platform | NO | OK |
| Viking | NO | OK |
| Discovery | NO | OK |
| Flash | NO | OK |

**Result**: 1 of 9 has Non-Circumvention (the broker NDA)

### 6.5 Return of Confidential Information (Allow retaining copy)

| NDA | Allows retention | Status |
|-----|------------------|--------|
| Ampere | Yes - "legal or regulatory compliance" + "electronic backup" | OK |
| Toro | Yes - "required by law" + "archived computer backup" | OK |
| Buyer & Seller | Yes - "backup server" + "document retention policy" | OK |
| Rembrandt | Yes - "archived computer system backups" + "applicable law" | OK |
| Crimson | Yes - "required... pursuant to applicable law" + "retention policies" | OK |
| Platform | Yes - "single copy for documentary purposes" + "electronic records" | OK |
| Viking | Yes - "required by law" + "back-up systems" | OK |
| Discovery | Yes - "required to comply with applicable law" + "backed-up" | OK |
| Flash | Yes - "normal document retention practices" + "archival" | OK |

**Result**: 100% consistency - All allow retaining copies

### 6.6 Private Equity Acknowledgement

| NDA | Has PE Acknowledgement | Observation |
|-----|------------------------|-------------|
| Ampere | NO | - |
| Toro | PARTIAL | Has similar "Portfolio Companies" clause |
| Buyer & Seller | NO | - |
| Rembrandt | NO | - |
| Crimson | NO | - |
| Platform | NO | - |
| Viking | PARTIAL | Has clause about portfolio companies at the end |
| **Discovery** | **YES - COMPLETE** | Section 14 with text almost identical to required |
| Flash | NO | - |

**Result**: Only 1 of 9 has the complete clause (Discovery)

---

## 7. Additional Findings from NDAs

### 7.1 Common Clauses Identified (not in original requirements)

These clauses appear in most NDAs but were not mentioned in the requirements:

| Clause | Frequency | Description | Impact |
|--------|-----------|-------------|--------|
| No Contact | 9/9 | No contacting employees/clients/suppliers without consent | **Seller-Friendly** - Restricts buyer access |
| No Warranty | 9/9 | No warranties on information accuracy | **Seller-Friendly** - Seller doesn't guarantee truthfulness |
| Definitive Agreement | 9/9 | No obligation until definitive agreement | **Balanced** - Protects both parties |
| Equitable Relief | 9/9 | Right to injunctive relief | **Balanced** - Both parties can seek injunction |
| Return/Destroy | 9/9 | Return or destroy information | **Seller-Friendly** - Requires buyer to eliminate information |
| Assignment | 8/9 | Assignment restrictions | **Balanced** - Prevents unauthorized transfers |
| Jury Waiver | 1/9 | Jury trial waiver | **Market Standard** - Common in commercial contracts |
| Financing Sources | 1/9 | Financing source restrictions | **Seller-Friendly** - Limits PE buyer's ability to finance |

### 7.2 Atypical NDA Detected

**"NDA - Buyer & Seller Intro & CA (Halmos Redline)"** is significantly different:

- It's a **business broker** NDA (Pacifica Advisors)
- Has **Non-Circumvention clause** (Section 4) - FLAG
- Includes references to **California Civil Code** (real estate)
- Includes **Agency Disclosure** (Exhibit 1 and 2)
- Simpler structure, oriented to small business transactions

**Recommendation**: This type of NDA should be flagged as "different type" - it's not a traditional M&A NDA.

---

## 8. Actionables from Original Text

### Documented Next Steps

| Responsible | Action | Status |
|-------------|--------|--------|
| **Andrew** | Provide Sample NDA + key terms | **COMPLETED** |
| **Andrew** | Send library of approved NDAs | **COMPLETED** |
| **Andrew** | Send investment thesis (SIM) | Pending |
| **Justin** | Prepare ballpark cost estimate | Pending |
| **Both** | Dec 17th 10:30 AM ET meeting | To be confirmed |

### Specific Action Items

| Item | Description | Status |
|------|-------------|--------|
| 1 | Email Andrew AI roundtable notes | - |
| 2 | Email Justin NDA + key clauses + investment thesis | Partial (NDAs received) |
| 3 | Send Andrew Dec 17 10:30 ET follow-up invite | - |

---

## 9. What is NOT Defined in the Text

The client did NOT specify:

- Technology stack
- Architecture
- Development phases
- Timeline
- Exact budget (only "ballpark estimate")
- Number of users
- Expected NDA volume
- Output/report format
- Required integrations
- Security requirements
- Whether it's a web app, desktop, or API

---

*Document based on original text + analysis of provided NDAs*
*Last updated: 2026-01-06*
