# NDA Analyzer - Sample NDA Analysis

> Findings document for client consultations

---

## 1. Executive Summary

**9 NDAs** provided by Halmos Capital were analyzed as "examples of NDAs they have become comfortable with".

| Metric | Result |
|--------|--------|
| Total NDAs analyzed | 9 |
| NDAs without flags (6 core clauses) | 8 |
| NDAs with flags | 1 |
| Flag detected | Non-Circumvention |

---

## 2. NDA Library Analyzed

| # | Project | Date | Advisor/Counterparty |
|---|---------|------|----------------------|
| 1 | Ampere | Oct 6, 2025 | Paralign Capital Consultants |
| 2 | Toro | Oct 24, 2025 | Halmos Capital (Own Form NDA) |
| 3 | Buyer & Seller | - | Pacifica Advisors (Broker) |
| 4 | Rembrandt | Mar 21, 2025 | Rohner Intermediate, Inc. |
| 5 | Crimson | Aug 6, 2025 | Selling company (unnamed) |
| 6 | Platform | Aug 6, 2025 | Amherst Partners |
| 7 | Viking | Aug 6, 2025 | Amherst Capital Partners |
| 8 | Discovery | Aug 22, 2025 | Forvis Mazars Capital Advisors |
| 9 | Flash | Oct 24, 2025 | Prairie Capital Advisors |

---

## 3. Results by Clause (6 Core Criteria)

> **Terminology**: Standard M&A nomenclature is used: **Buyer-Friendly**, **Seller-Friendly**, **Market Standard**, **Balanced**.

### 3.1 Governing Law (Must be Delaware)

**Impact**: **Market Standard** - Delaware benefits both parties (predictability, Court of Chancery)

| NDA | Value Found | Status |
|-----|-------------|--------|
| Ampere | "State of Delaware" | OK |
| Toro | "State of Delaware" | OK |
| Buyer & Seller | "State of Delaware" | OK |
| Rembrandt | "State of Delaware" | OK |
| Crimson | "State of Delaware" | OK |
| Platform | "State of Delaware" | OK |
| Viking | "State of Delaware" | OK |
| Discovery | "State of Delaware" | OK |
| Flash | "State of Delaware" | OK |

**Result: 9/9 OK (100%)**

---

### 3.2 Term (Must be 2 years or less)

**Impact**: **Buyer-Friendly** if ≤2 years. Long term (>2 years) is **Seller-Friendly**.

| NDA | Value Found | Status |
|-----|-------------|--------|
| Ampere | "two (2) years" | OK |
| Toro | "two (2) years" | OK |
| Buyer & Seller | "two years" | OK |
| Rembrandt | "two (2) years" | OK |
| Crimson | "two (2) years" | OK |
| Platform | "second (2nd) anniversary" | OK |
| Viking | "two years" | OK |
| Discovery | "two (2) years" | OK |
| Flash | "two (2) years" | OK |

**Result: 9/9 OK (100%)**

---

### 3.3 Non-Solicit (Must allow general advertisements and non-directed employment agencies)

**Impact**: **Buyer-Friendly** if has exceptions. Without exceptions is **Seller-Friendly**.

| NDA | Exception Found | Status |
|-----|-----------------|--------|
| Ampere | "general public advertisements or search firms (in each case, not directed at...)" | OK |
| Toro | "general job advertisements... recruiting firm or organization... not instructed to target" | OK |
| Buyer & Seller | "general job advertisement or recruiting agency" | OK |
| Rembrandt | "general solicitations for employment by means of advertisements... not specifically directed" | OK |
| Crimson | "general solicitation such as an advertisement... not specifically targeted" | OK |
| Platform | "general public employment solicitation, including search agencies, not targeted" | OK |
| Viking | "general solicitation, including the use of general advertisements and employment agencies" | OK |
| Discovery | "generalized solicitation... through the use of media, advertisements, professional search firms" | OK |
| Flash | "general solicitation for employment... not specifically directed" | OK |

**Result: 9/9 OK (100%)**

---

### 3.4 Non-Circumvention (FLAG if exists)

**Impact**: **Seller-Friendly** - Creates liability for the buyer. Protects broker/seller fees.

| NDA | Has Non-Circumvention? | Status |
|-----|------------------------|--------|
| Ampere | NO | OK |
| Toro | NO | OK |
| **Buyer & Seller** | **YES - Section 4 "NON-CIRCUMVENTION AGREEMENT"** | **FLAG** |
| Rembrandt | NO | OK |
| Crimson | NO | OK |
| Platform | NO | OK |
| Viking | NO | OK |
| Discovery | NO | OK |
| Flash | NO | OK |

**Result: 8/9 OK, 1/9 FLAG**

#### FLAG Detail - Buyer & Seller NDA

Exact text of Non-Circumvention clause found:

```
4. NON-CIRCUMVENTION AGREEMENT: The Seller has entered into an agreement
providing that Seller shall pay a fee to the Broker if, during the term of
that agreement or up to twenty-four months thereafter, the Business is
transferred to a buyer introduced by the Broker. Buyer shall conduct all
inquiries into and discussions about the Business solely through the Broker
identified above and shall not directly contact the Seller or the Seller's
representatives without written authorization by the Broker. Should Buyer
or any person or entity affiliated with Buyer purchase all or part of the
Business, acquire any interest in, or become affiliated in any capacity with
the Business without the involvement of the Broker or in any way interfere
with either Broker's right to a fee, Buyer shall be liable to the Broker
for such fee.
```

---

### 3.5 Return of Confidential Information (Must allow retaining at least one copy for archives)

**Impact**: **Buyer-Friendly** if allows retention (compliance). Without retention is **Seller-Friendly**.

| NDA | Allows Retention | Key Text | Status |
|-----|------------------|----------|--------|
| Ampere | YES | "legal or regulatory compliance" + "electronic backup" | OK |
| Toro | YES | "required by law" + "archived computer backup" | OK |
| Buyer & Seller | YES | "backup server" + "document retention policy" | OK |
| Rembrandt | YES | "archived computer system backups" + "applicable law" | OK |
| Crimson | YES | "pursuant to applicable law" + "retention policies" | OK |
| Platform | YES | "single copy for documentary purposes" + "electronic records" | OK |
| Viking | YES | "required by law" + "back-up systems" | OK |
| Discovery | YES | "required to comply with applicable law" + "backed-up" | OK |
| Flash | YES | "normal document retention practices" + "archival" | OK |

**Result: 9/9 OK (100%)**

---

### 3.6 Private Equity Acknowledgement (Desirable - suggest adding if not present)

**Impact**: **Buyer-Friendly** - Protects PE buyer from restrictions on portfolio companies. Its absence is **Seller-Friendly**.

| NDA | Has PE Acknowledgement? | Observation |
|-----|-------------------------|-------------|
| Ampere | NO | - |
| Toro | PARTIAL | Has "Portfolio Companies" clause |
| Buyer & Seller | NO | - |
| Rembrandt | NO | - |
| Crimson | NO | - |
| Platform | NO | - |
| Viking | PARTIAL | Has clause about portfolio companies at the end |
| **Discovery** | **YES - COMPLETE** | Section 14 "Private Equity Acknowledgement" |
| Flash | NO | - |

**Result: 1/9 complete, 2/9 partial, 6/9 absent**

#### Detail - Discovery NDA (Complete PE Acknowledgement)

```
14. Private Equity Acknowledgement. The Company acknowledges that (i) you and
your affiliates are engaged in the business of private equity investing and
may from time to time invest in entities that develop and utilize technologies,
products or services that are similar to or competitive with those of the
Company, and (ii) except insofar as this Agreement restricts the disclosure
of the Evaluation Material, this Agreement shall not prevent you or your
affiliates from (a) engaging in or operating any business, (b) entering into
any agreement or business relationship with any third party, or (c) evaluating
or engaging in investment discussions with, or investing in, any third party,
whether or not competitive with the Company or its affiliates...
```

---

## 4. Additional Clauses Detected (Not in original requirements)

These clauses appear in some NDAs and could be relevant:

### 4.1 Jury Waiver

**Impact**: **Market Standard** - Common in sophisticated commercial contracts.

| NDA | Has Jury Waiver? |
|-----|------------------|
| Ampere | NO |
| Toro | NO |
| Buyer & Seller | NO |
| Rembrandt | NO |
| **Crimson** | **YES** |
| Platform | NO |
| Viking | NO |
| Discovery | NO |
| Flash | NO |

#### Text in Crimson:

```
7. Jury Waiver. EACH OF THE PARTIES TO THIS AGREEMENT IRREVOCABLY AND
UNCONDITIONALLY WAIVES THE RIGHT TO A TRIAL BY JURY IN ANY ACTION, SUIT
OR PROCEEDING ARISING OUT OF, IN CONNECTION WITH, OR RELATING TO THIS
AGREEMENT...
```

---

### 4.2 Financing Sources Restrictions

**Impact**: **Seller-Friendly** - Limits PE buyer's ability to obtain financing or form club deals.

| NDA | Has Financing Sources restrictions? |
|-----|-------------------------------------|
| Ampere | NO |
| **Toro** | **YES** |
| Buyer & Seller | NO |
| Rembrandt | NO |
| Crimson | NO |
| Platform | NO |
| Viking | NO |
| Discovery | NO |
| Flash | NO |

#### Text in Toro:

```
Financing Sources: You shall not, and shall direct your representatives not to,
without the prior written consent of the Company, (a) communicate with any
potential bidding partners or financing sources regarding a Possible Transaction
or (b) enter into any agreement, arrangement or understanding... with any actual
or potential bidding partners or financing sources that could reasonably be
expected to limit, restrict, restrain, or otherwise impair... the ability of
such partners or financing sources to provide financing or other assistance to
any other person in any other possible transaction involving the Company...
```

---

## 5. Atypical NDA: Buyer & Seller

This NDA is fundamentally different from the other 8:

| Aspect | Other 8 NDAs | Buyer & Seller |
|--------|--------------|----------------|
| **Type** | M&A / PE | Business Broker |
| **Origin** | Seller/Advisor | Broker (Pacifica Advisors) |
| **Non-Circumvention** | NO | YES |
| **Additional content** | - | California Civil Code, Agency Disclosure |
| **Length** | 10-15 pages | 3-4 pages |
| **Legal complexity** | High | Medium |

### Why is it in the library?

**Hypothesis**: This NDA was included as an **example of a case with flag** that the analyzer should detect, not as a "clean" NDA.

---

## 6. Findings Summary

### Flags Detected (Core Criteria)

| Flag | NDA | Severity |
|------|-----|----------|
| Non-Circumvention present | Buyer & Seller | **HIGH** (per requirements) |

### Additional Clauses to Consider

| Clause | NDA | Include as flag? |
|--------|-----|------------------|
| Jury Waiver | Crimson | **TO CONSULT** |
| Financing Sources Restrictions | Toro | **TO CONSULT** |

### Notable Absences

| Clause | Frequency | Suggested action |
|--------|-----------|------------------|
| Complete PE Acknowledgement | 1/9 (11%) | Suggest adding in 8 of 9 |

---

## 7. Questions for Client

### About Buyer & Seller NDA (Broker)

1. Was this NDA intentionally included as an **example of a case with flag**?
2. Do you receive broker NDAs frequently, or was this an exceptional case?
3. Should the analyzer classify/identify the **NDA type** (M&A vs Broker)?

### About Additional Clauses

4. Should **Jury Waiver** be flagged if present? (appears in Crimson)
5. Should **Financing Sources Restrictions** be flagged? (appears in Toro, which is your Form NDA)
6. Are there other clauses we should add to the analysis?

### About Prioritization

7. Do all flags have the same severity or are there **deal-breakers vs warnings**?
8. Is Non-Circumvention an automatic deal-breaker or context-dependent?

### About PE Acknowledgement

9. Should we **suggest adding** PE Acknowledgement in all NDAs that don't have it?
10. Or only in specific cases?

---

## 8. Additional Contractual Risks (Research)

> See full document: **04_NDA_RISK_RESEARCH.md**

Research was conducted with verifiable sources on contractual risks in M&A NDAs. Summary of identified risks:

### Critical and High Risks

| Risk | Severity | Found in sample NDAs |
|------|----------|----------------------|
| Break-up fees / Termination fees | CRITICAL | NO |
| Standstill provisions | HIGH | NO |
| Non-circumvention | HIGH | YES (Buyer & Seller) |
| Financing source restrictions | HIGH | YES (Toro) |
| Portfolio company restrictions | HIGH | Partial (no PE Ack in 8/9) |
| Liquidated damages | HIGH | NO |

### Medium Risks

| Risk | Severity | Found in sample NDAs |
|------|----------|----------------------|
| Residual clauses | MEDIUM | NOT explicitly detected |
| Exclusivity / No-shop | MEDIUM | NO |
| Perpetual obligations | MEDIUM | NO (all are 2 years) |
| Overly broad non-solicit | MEDIUM | NO (all have exceptions) |
| Jury Waiver | MEDIUM | YES (Crimson) |

### Relevant Legal Cases

| Case | Relevance |
|------|-----------|
| *Martin Marietta v. Vulcan (2012)* | "Use" clauses can operate as de facto standstill |
| *Space Data v. Google* (N.D. Cal. 2017) | Residual clauses make proving breach difficult (NOT Delaware - persuasive only) |
| *Goodrich Capital v. Vector Capital* (S.D.N.Y. 2012) | Non-circumvention can create $3.5M+ liability |

**Sources**: 31 law firm articles and legal publications (see doc 04).

---

## 9. Suggested Next Steps

1. **Confirm interpretation** of Buyer & Seller NDA with client
2. **Define severity** of flags (deal-breaker vs warning)
3. **Decide** whether to include Jury Waiver and Financing Restrictions in analysis
4. **Validate** that the 9 NDAs are representative of actual volume
5. **Review** additional risks from document 04 with client

---

## 10. Related Documents

| Doc | Name | Content |
|-----|------|---------|
| 01 | CLIENT_REQUIREMENTS | Raw client data |
| **02** | **NDA_ANALYSIS_FINDINGS** | **This document** |
| 03 | COMPLETE_PLAN | Plan with proposals |
| 04 | NDA_RISK_RESEARCH | Risks with 31 verifiable sources |
| 05 | LEGAL_DATA_SOURCES | Sources for Delaware law (MCP/Agent) |

---

*Document generated: 2026-01-06*
*Last updated: 2026-01-06*
*For: Client consultations (Halmos Capital)*
