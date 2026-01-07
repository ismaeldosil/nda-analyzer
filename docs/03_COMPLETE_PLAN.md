# NDA Analyzer - Complete Plan (Requirements + Proposals)

> This document includes client requirements PLUS proposals and suggestions for negotiation. Sections marked with [PROPOSAL] are not in the original text.

---

## 1. Client Context

- **Type**: Small Independent Sponsor firm (Halmos Capital)
- **Portfolio**: Few portcos
- **Team**: Small, looking for efficiencies
- **Requested Projects**: NDA Analyzer + SIM Analyzer (separate)

---

## 2. Strategic Vision

### From client:
- Simple tool, "door opener"
- Possibly free or low monthly fee
- To attract users to the REEA platform

### [PROPOSAL] Business model to define:

| Option | Description | Pros | Cons |
|--------|-------------|------|------|
| **Free** | 100% free | Maximum adoption | No direct revenue |
| **Freemium** | Basic free, premium features paid | Balance adoption/revenue | Complexity |
| **Low-cost subscription** | Low monthly fee ($X/month) | Predictable revenue | Entry barrier |
| **Usage-based** | Pay per NDA analyzed | Scales with use | Unpredictable |

---

## 3. Functional Requirements

### 3.1 Clauses to Analyze (From client)

> **Standard M&A Terminology**: **Buyer-Friendly**, **Seller-Friendly**, **Market Standard**, **Balanced**.

| # | Clause | Criteria | Flag if... | Impact |
|---|--------|----------|------------|--------|
| 1 | **Governing Law** | State of Delaware | Different from Delaware | **Market Standard** |
| 2 | **Term** | 2 Years or less | Greater than 2 years | **Buyer-Friendly** if ≤2 years |
| 3 | **Non-Solicit** | Allow general ads and non-directed agencies | Additional restrictions | **Buyer-Friendly** if has exceptions |
| 4 | **Non-Circumvention** | Should not exist | Exists | **Seller-Friendly** |
| 5 | **Return of Confidential Info** | Allow retaining copy for archives | Doesn't allow it | **Buyer-Friendly** if allows |
| 6 | **PE Acknowledgement** | Specific text (see appendix) | Doesn't exist (suggest adding) | **Buyer-Friendly** |

### 3.2 Anomaly Detection (From client)

- Use ChatGPT-like capabilities
- Flag unusual clauses
- Example: hidden break-up fees

### 3.3 PE Acknowledgement Widget (From client)

- Functionality to insert PE Acknowledgement text into NDAs
- "Would be great to create a widget to do that"

---

## 4. Reference NDA Analysis (9 documents)

### 4.1 Available Library

| # | Project | File | Type |
|---|---------|------|------|
| 1 | Ampere | `Project Ampere - Confidentiality Agreement_vF (Edits).docx` | Standard M&A |
| 2 | Toro | `Project Toro - Form of Non-Disclosure Agreement (1).docx` | **Form NDA** |
| 3 | - | `NDA - Buyer & Seller Intro & CA (Halmos Redline) (1).docx` | Broker (atypical) |
| 4 | Rembrandt | `Project REMBRANDT - NDA - Halmos Capital (1).docx` | Standard M&A |
| 5 | Crimson | `Project Crimson - Confidentiality Agreement (NDA)_Halmos Capital (1).docx` | Standard M&A |
| 6 | Platform | `Project Platform - NDA (1).DOCX` | Standard M&A |
| 7 | Viking | `Project Viking - NDA (Halmos Redline) (1).docx` | M&A with redlines |
| 8 | Discovery | `Project Discovery NDA (1).docx` | M&A with PE Ack |
| 9 | Flash | `Project Flash - Prospective Buyer NDA (1).docx` | Standard M&A |

### 4.2 Criteria Validation Against Real NDAs

| Criteria | Result | Observation |
|----------|--------|-------------|
| **Governing Law = Delaware** | 9/9 (100%) | All use Delaware |
| **Term <= 2 years** | 9/9 (100%) | All are exactly 2 years |
| **Non-Solicit allows general ads** | 9/9 (100%) | All allow it |
| **Non-Circumvention absent** | 8/9 (89%) | Only "Buyer & Seller" has it |
| **Return allows retaining copy** | 9/9 (100%) | All allow it |
| **PE Acknowledgement present** | 1/9 (11%) | Only "Discovery" has it complete |

### 4.3 Additional Clauses Identified in NDAs

These clauses appear consistently but are not in the original requirements:

| Clause | Frequency | [PROPOSAL] Include in analysis? | Impact |
|--------|-----------|--------------------------------|--------|
| No Contact (employees/clients) | 9/9 | Consider | **Seller-Friendly** |
| No Warranty | 9/9 | Informative | **Seller-Friendly** |
| Definitive Agreement | 9/9 | Informative | **Balanced** |
| Equitable Relief | 9/9 | Informative | **Balanced** |
| Assignment Restrictions | 8/9 | Consider | **Balanced** |
| Jury Waiver | 1/9 | Flag if exists | **Market Standard** |
| Financing Sources Restrictions | 1/9 | Flag if exists | **Seller-Friendly** |

### 4.4 Atypical NDA Detected - Case Study

**"NDA - Buyer & Seller Intro & CA"** is fundamentally different:

| Aspect | Typical M&A NDAs | This NDA |
|--------|------------------|----------|
| Origin | Seller/Advisor | Broker (Pacifica Advisors) |
| Non-Circumvention | NO | YES (Section 4) |
| Additional content | N/A | California Civil Code, Agency Disclosure |
| Complexity | High (10-15 pages) | Medium (3-4 pages) |
| Transaction type | M&A PE/VC | Small business sale |

**[PROPOSAL]** The system should identify and classify NDAs by type:
- Type A: Standard M&A NDA (8 of 9)
- Type B: Broker/business sale NDA (1 of 9)

---

## 5. [PROPOSAL] Technical Architecture

### 5.1 Suggested Stack

```
┌─────────────────────────────────────────────────────────────┐
│                      FRONTEND                                │
│  [TBD: Next.js / React / Vue / etc.]                        │
│  - Document upload (DOCX priority)                          │
│  - Results dashboard                                         │
│  - Flag visualization                                        │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│                      BACKEND API                             │
│  [TBD: Node.js / Python / etc.]                             │
│  - Document parsing (mammoth/python-docx)                   │
│  - Orchestration                                             │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│                    AI/LLM LAYER                              │
│  [TBD: Claude / OpenAI / Azure OpenAI]                      │
│  - Clause extraction                                        │
│  - Semantic analysis                                         │
│  - Anomaly detection                                         │
│  - NDA type classification                                   │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│                    REFERENCE DATA                            │
│  - 9 reference NDAs (baseline)                              │
│  - Halmos Form NDA (Project Toro)                           │
│  - PE Acknowledgement text                                   │
└─────────────────────────────────────────────────────────────┘
```

### 5.2 Document Format

Based on the 9 received NDAs:

| Format | Count | Priority |
|--------|-------|----------|
| .docx | 8 | **High** |
| .DOCX | 1 | High |
| .pdf | 0 | Medium (future) |

**[PROPOSAL]** POC should prioritize DOCX over PDF.

### 5.3 Pending Technical Decisions

| Decision | Options | Cost Impact |
|----------|---------|-------------|
| LLM Provider | Claude API / OpenAI / Azure | Variable per token |
| Frontend Framework | Next.js / React / Vue | Similar |
| Backend | Node.js / Python FastAPI / Go | Similar |
| Hosting | Vercel / AWS / GCP / Azure | Variable |
| Database | PostgreSQL / MongoDB / None | Low |
| Doc Storage | S3 / Local / Don't store | Compliance dependent |

---

## 6. [PROPOSAL] Development Phases

### Phase 1: Basic POC
- [ ] Document upload (DOCX)
- [ ] Text extraction
- [ ] 6 core clauses analysis
- [ ] Report with flags (OK / FLAG / MISSING)
- [ ] Minimal functional UI
- [ ] Comparison with Form NDA (Project Toro)

### Phase 2: Enhanced POC
- [ ] PDF support (non-scanned)
- [ ] Anomaly detection with LLM
- [ ] NDA type classification (M&A vs Broker)
- [ ] Widget to insert PE Acknowledgement
- [ ] Export report
- [ ] Additional clauses analysis (No Contact, Assignment, etc.)

### Phase 3: Production MVP
- [ ] User authentication
- [ ] Multi-tenancy (if applicable)
- [ ] Configurable rules per client
- [ ] Analysis history
- [ ] Polished UI
- [ ] OCR for scanned PDFs

### Phase 4: Full Production
- [ ] Public API
- [ ] Integrations (CRM, email, etc.)
- [ ] Batch processing
- [ ] Analytics and reporting
- [ ] Audit trail
- [ ] Machine learning to improve detection

---

## 7. [PROPOSAL] Effort Estimation (T-Shirt Sizing)

| Phase | Size | Scope |
|-------|------|-------|
| Basic POC | **S** | 6 clauses + minimal UI + DOCX |
| Enhanced POC | **M** | + Anomalies + Classification + Widget + PDF |
| Production MVP | **L** | + Auth + Config + History + OCR |
| Full Production | **XL** | + API + Integrations + Batch + ML |

> Note: Client requested "ballpark estimate" and "t-shirt sizing" - these sizes need to be translated to hours/cost.

---

## 8. [PROPOSAL] Detailed Analysis Logic

### 8.1 Extraction Rules by Clause

| Clause | Keywords to search | Logic |
|--------|-------------------|-------|
| **Governing Law** | "governed by", "construed in accordance", "laws of" | Extract state/jurisdiction |
| **Term** | "shall terminate", "period of", "years from the date" | Extract numeric duration |
| **Non-Solicit** | "solicit", "hire", "employ", "recruit" | Look for exceptions (general ads) |
| **Non-Circumvention** | "circumvent", "circumvention", "non-circumvent" | Detect existence |
| **Return of Info** | "return", "destroy", "retain", "archival", "backup" | Verify retention permission |
| **PE Acknowledgement** | "private equity", "portfolio companies", "competitive" | Semantic match with reference text |

### 8.2 Anomaly Patterns to Detect (Based on Research)

> Source: **04_NDA_RISK_RESEARCH.md** (31 verified law firm sources)

#### Tier 1 - Critical Risk (Deal-breaker)

| Anomaly | Description | Keywords | Impact |
|---------|-------------|----------|--------|
| **Break-up fee** | Payment obligation if deal doesn't close | "break-up", "termination fee", "reverse break" | **Seller-Friendly** |

#### Tier 2 - High Risks (FLAG for negotiation)

| Anomaly | Description | Keywords | Impact |
|---------|-------------|----------|--------|
| **Non-Circumvention** | Prevents direct contact (already in requirements) | "circumvent", "non-circumvent" | **Seller-Friendly** |
| **Standstill provision** | Acquisition action restriction | "standstill", "shall not acquire", "proxy" | **Seller-Friendly** |
| **Liquidated damages** | Predetermined fixed amounts for breach | "liquidated damages", "penalty", "fixed sum" | **Seller-Friendly** |
| **Financing restrictions** | Limits financing sources | "financing source", "consortium", "club deal" | **Seller-Friendly** |
| **Portfolio company restrictions** | NDA applies to portcos without PE Ack | "portfolio company", "affiliate" | **Seller-Friendly** |

#### Tier 3 - Medium Risks (Informative)

| Anomaly | Description | Keywords | Impact |
|---------|-------------|----------|--------|
| **Residual clause** | Allows use of info in "unaided memory" | "residual", "unaided memory" | **Buyer-Friendly** |
| **Exclusivity / No-shop** | Prevents negotiating with others | "exclusivity", "no-shop" | **Buyer-Friendly** |
| **Perpetual obligations** | Term > 3 years or indefinite | "perpetual", "indefinite", "shall survive" | **Seller-Friendly** |
| **Overly broad non-solicit** | Without standard exceptions | Scope analysis | **Seller-Friendly** |
| **Jury Waiver** | Jury trial waiver | "waive", "jury" | **Market Standard** |
| **Damages waiver** | Consequential damages waiver | "consequential damages", "lost profits" | **Buyer-Friendly** |

#### Reference Legal Cases

| Case | Year | Relevance | Source |
|------|------|-----------|--------|
| *Martin Marietta v. Vulcan Materials* | 2012 | Use clause = backdoor standstill | Delaware Court |
| *Space Data Corp. v. Google* | 2017 | Residual clause makes proof difficult (NOT Delaware - persuasive only) | N.D. California |
| *Goodrich Capital v. Vector Capital* | 2012 | Non-circumvention = $3.5M liability | S.D.N.Y. |

---

## 9. [PROPOSAL] Security Considerations

| Aspect | Recommendation |
|--------|----------------|
| Data in transit | HTTPS/TLS mandatory |
| Data at rest | Encryption if documents are stored |
| Retention | Define policy (are NDAs stored?) |
| LLM Privacy | Verify chosen provider's policies |
| Access | Authentication required (or not if it's a public "door opener") |
| Compliance | SOC2 / GDPR if enterprise clients |

---

## 10. [PROPOSAL] Identified Risks

| Risk | Probability | Impact | Mitigation |
|------|-------------|--------|------------|
| NDA format variability | High | Medium | Robust parser + flexible LLM |
| Analysis precision | Medium | High | Testing with 9 reference NDAs |
| Low quality scanned PDFs | Medium | Medium | Quality OCR + fallback |
| Scope creep | High | High | Clearly define POC scope |
| False positives/negatives | Medium | High | Calibration with existing library |
| Atypical NDAs (broker type) | Low | Medium | Automatic type classification |

---

## 11. Actionables

### From original text (existing commitments)

| # | Responsible | Action | Status |
|---|-------------|--------|--------|
| 1 | Andrew | Send sample NDA + key terms | **COMPLETED** |
| 2 | Andrew | Send library of approved NDAs | **COMPLETED** (9 NDAs) |
| 3 | Andrew | Send investment thesis (for SIM) | Pending |
| 4 | Justin | Prepare ballpark cost estimate | Pending |
| 5 | Justin | Send NDA/SIM t-shirt sizing | Pending |
| 6 | Both | Dec 17, 10:30 AM ET meeting | To be confirmed |

### [PROPOSAL] Additional suggested actionables

| # | Responsible | Action | Priority |
|---|-------------|--------|----------|
| 7 | REEA | Define technology stack | High |
| 8 | REEA | Choose LLM provider | High |
| 9 | Client | Confirm flag prioritization (deal-breaker vs warning) | High |
| 10 | Client | Confirm if "Buyer & Seller" NDA is valid case or exception | High |
| 11 | Client | Define expected NDA volume | Medium |
| 12 | Client | Confirm if users/auth needed | Medium |
| 13 | Both | Define business model (free/paid) | Medium |
| 14 | REEA | Evaluate integration with existing REEA platform | Medium |
| 15 | Client | Confirm desired output format | Low |
| 16 | Both | Define expected SLA/response time | Low |

---

## 12. [PROPOSAL] Questions for Client

### Functional (Updated)
1. Do the 6 clauses have equal priority or are there deal-breakers?
2. Should PE Acknowledgement always be suggested or only when protections are missing?
3. Is the "Buyer & Seller" (broker) NDA a case they need to handle or an exception?
4. Should additional clauses (No Contact, Jury Waiver, Financing) be included in analysis?
5. Can the system "auto-approve" or is it always a recommendation?

### Operational
6. How many NDAs do you analyze per week/month approximately?
7. Who would use the tool? (roles, quantity)
8. Do you need history of analyzed NDAs?
9. Is there a preferred report format?

### Technical
10. Is there a preferred technology stack or restrictions?
11. Integration with existing systems? (CRM, email, etc.)
12. Specific compliance requirements?
13. Is the tool standalone or part of REEA platform?

---

## Appendix A: PE Acknowledgement Text (Reference)

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

---

## Appendix B: Reference NDAs - Executive Summary

| NDA | Gov Law | Term | Non-Solicit OK | No Circumvent | Retain Copy | PE Ack |
|-----|---------|------|----------------|---------------|-------------|--------|
| Ampere | DE | 2y | OK | OK | OK | NO |
| Toro (Form) | DE | 2y | OK | OK | OK | Partial |
| Buyer&Seller | DE | 2y | OK | **FLAG** | OK | NO |
| Rembrandt | DE | 2y | OK | OK | OK | NO |
| Crimson | DE | 2y | OK | OK | OK | NO |
| Platform | DE | 2y | OK | OK | OK | NO |
| Viking | DE | 2y | OK | OK | OK | Partial |
| Discovery | DE | 2y | OK | OK | OK | **YES** |
| Flash | DE | 2y | OK | OK | OK | NO |

---

## Legend

- **No mark**: Information from client's original text or analysis of provided documents
- **[PROPOSAL]**: Additional suggestions for negotiation/definition

---

## Related Documents

| Doc | Name | Content |
|-----|------|---------|
| 01 | CLIENT_REQUIREMENTS | Raw client data |
| 02 | NDA_ANALYSIS_FINDINGS | 9 NDA analysis + questions |
| **03** | **COMPLETE_PLAN** | **This document** |
| 04 | NDA_RISK_RESEARCH | Risks with 31 verifiable sources |
| 05 | LEGAL_DATA_SOURCES | Sources for Delaware law (MCP/Agent) |

---

*Document generated: 2026-01-06*
*Last updated: 2026-01-06*
*Next review: Dec 17, 10:30 AM ET meeting*
