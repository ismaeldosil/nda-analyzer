# Legal Data Sources for NDA Analyzer

> Resources for obtaining Delaware and other states' legal data for the agent/MCP or as project reference.

---

## 1. Executive Summary

| Category | Best Option | Format | Cost |
|----------|-------------|--------|------|
| **Delaware Statutes** | delcode.delaware.gov (official) + scraping | HTML | Free |
| **Case Law (US)** | Harvard CAP / CourtListener | JSON/API | Free |
| **Legal NLP Dataset** | Pile of Law | Parquet | Free |
| **State Codes (General)** | State Decoded | XML/API | Free |

---

## 2. Delaware-Specific Sources

### 2.1 Delaware Code Online (Official) - RECOMMENDED

**URL**: [delcode.delaware.gov](https://delcode.delaware.gov/)

| Aspect | Detail |
|--------|--------|
| **Source** | Division of Research, Legislative Council |
| **Format** | HTML (no bulk download) |
| **Relevant Titles** | Title 6 (Commerce/DUTSA), Title 8 (Corporations/DGCL) |
| **Updates** | Official and up-to-date |

**Key sections for NDAs**:
```
Title 6, Chapter 20 - Delaware Uniform Trade Secrets Act (DUTSA)
  § 2001 - Definitions
  § 2002 - Injunctive relief
  § 2003 - Damages
  § 2004 - Attorney's fees
  § 2005 - Preservation of secrecy
  § 2006 - Statute of limitations
  § 2007 - Effect on other law

Title 8 - General Corporation Law (DGCL)
  Chapter 1 - General Corporation Law
```

**Extraction strategy**:
- Manual scraping of relevant sections (Title 6 Ch 20, Title 8)
- Create local JSON/MD file with key sections
- Update periodically from official source

**Advantages**:
- Official and authoritative source
- Always up-to-date
- Free

**Limitations**:
- No bulk download offered
- Requires scraping or manual extraction

---

## 3. Large-Scale Datasets

### 3.1 Pile of Law (Stanford/Harvard)

**URLs**:
- Dataset: [huggingface.co/datasets/pile-of-law/pile-of-law](https://huggingface.co/datasets/pile-of-law/pile-of-law)
- GitHub: [github.com/Breakend/PileOfLaw](https://github.com/Breakend/PileOfLaw)
- Paper: [arxiv.org/abs/2207.00220](https://arxiv.org/abs/2207.00220)

| Aspect | Detail |
|--------|--------|
| **Size** | 256GB+ |
| **Content** | Court opinions, contracts, statutes, regulations, casebooks |
| **Format** | Parquet (Hugging Face) |
| **License** | CC BY-NC-SA 4.0 |
| **Ideal use** | Pretraining legal LLMs, NLP research |

**Included content**:
- Court opinions and filings
- Government agency publications
- Contracts
- Statutes and regulations
- Legal casebooks

---

### 3.2 Harvard Caselaw Access Project (CAP)

**URLs**:
- Main: [case.law](https://case.law/)
- API Docs: [case.law/api](https://case.law/api/)
- Bulk Data: [case.law/bulk](https://case.law/bulk/)

| Aspect | Detail |
|--------|--------|
| **Content** | 6.7M+ cases, 360 years of US legal history |
| **Coverage** | All states, federal courts |
| **Format** | JSON via API, bulk downloads |
| **License** | Free for research |

**Limitation**: Case law only (jurisprudence), not statutes.

---

### 3.3 CourtListener / Free Law Project

**URLs**:
- Main: [courtlistener.com](https://www.courtlistener.com/)
- API: [courtlistener.com/help/api](https://www.courtlistener.com/help/api/)
- Bulk Data: [courtlistener.com/help/api/bulk-data](https://www.courtlistener.com/help/api/bulk-data/)

| Aspect | Detail |
|--------|--------|
| **Content** | Case law, oral arguments, judges database |
| **Jurisdictions** | 406 of 423 US jurisdictions |
| **Time range** | 1754 - present |
| **Format** | JSON API, PostgreSQL bulk exports |
| **License** | Free (501c3 nonprofit) |

---

## 4. Tools and Frameworks

### 4.1 State Decoded

**URL**: [github.com/statedecoded/statedecoded](https://github.com/statedecoded/statedecoded)

| Aspect | Detail |
|--------|--------|
| **Type** | Web app for displaying laws |
| **Features** | Searchable, API, bulk downloads, semantic analysis |
| **Implementations** | Virginia, Chicago, San Francisco, others |
| **Output format** | XML, JSON, API |

**Use**: Framework for creating your own laws portal with API.

---

### 4.2 OpenStatute / us-statutes

**URLs**:
- Web: [openstatute.org](https://openstatute.org)
- GitHub: [github.com/openstatute/us-statutes](https://github.com/openstatute/us-statutes)

| Aspect | Detail |
|--------|--------|
| **Content** | US state codes in JSON |
| **Format** | Structured JSON |
| **Access** | Direct GitHub |

---

### 4.3 awesome-legal-data (Curated List)

**URL**: [github.com/openlegaldata/awesome-legal-data](https://github.com/openlegaldata/awesome-legal-data)

Curated list of datasets and resources for legal text processing. Includes:
- Open datasets
- Commercial APIs
- Legal NLP tools
- Jurisdiction-specific resources

---

## 5. Commercial APIs

### 5.1 Fastcase Legal Data API

**URL**: [fastcase.com/solutions/legal-data-api](https://www.fastcase.com/solutions/legal-data-api/)

| Aspect | Detail |
|--------|--------|
| **Content** | Statutes, regulations, case law |
| **Format** | JSON, XML, LDML |
| **Filters** | By type (statutes, regulations), keywords |
| **Cost** | Commercial (contact for pricing) |

---

### 5.2 LegiScan API

**URL**: [legiscan.com/legiscan](https://legiscan.com/legiscan)

| Aspect | Detail |
|--------|--------|
| **Content** | Bills, legislation tracking (50 states) |
| **Features** | Real-time updates, bulk datasets |
| **Cost** | Freemium |

**Note**: Tracking of active bills/legislation, not compiled code.

---

## 6. Academic Sources

### 6.1 Cornell Legal Information Institute (LII)

**URL**: [law.cornell.edu/states/delaware](https://www.law.cornell.edu/states/delaware)

| Aspect | Detail |
|--------|--------|
| **Content** | Delaware statutes, regulations, constitution |
| **Format** | HTML (no bulk) |
| **Updates** | Quarterly for regulations |

---

### 6.2 Justia

**URL**: [law.justia.com/codes/delaware](https://law.justia.com/codes/delaware/)

| Aspect | Detail |
|--------|--------|
| **Content** | Complete Delaware Code |
| **Format** | HTML (no bulk) |
| **Organization** | By title and chapter |

---

## 7. Project Recommendations

### For MCP Server / Agent

| Priority | Source | Reason |
|----------|--------|--------|
| **1** | delcode.delaware.gov | Official source, scraping of key sections |
| **2** | Pile of Law | Massive dataset for general legal context |
| **3** | Harvard CAP / CourtListener | Case law for jurisprudence |

### For Static Reference

| Use | Source |
|-----|--------|
| DUTSA (Trade Secrets) | delcode.delaware.gov Title 6 Ch 20 |
| DGCL (Corporations) | delcode.delaware.gov Title 8 |
| Delaware Case Law | Harvard CAP / CourtListener |

### Suggested Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    MCP Server Legal                         │
├─────────────────────────────────────────────────────────────┤
│  Local Files (JSON/Markdown)                                │
│  ├── Delaware Code (scraped from delcode.delaware.gov)      │
│  ├── Key sections: Title 6 Ch 20 (DUTSA), Title 8 (DGCL)    │
│  └── Indexed for fast retrieval                             │
├─────────────────────────────────────────────────────────────┤
│  WebFetch live                                              │
│  └── delcode.delaware.gov (official, for updates/validation)│
├─────────────────────────────────────────────────────────────┤
│  Optional: Pile of Law embeddings                           │
│  └── For semantic search on legal concepts                  │
└─────────────────────────────────────────────────────────────┘
```

---

## 8. Suggested Next Steps

1. [ ] Extract key sections from delcode.delaware.gov (Title 6 Ch 20, Title 8)
2. [ ] Create local JSON/MD file with NDA-relevant statutes
3. [ ] Evaluate whether to create dedicated MCP server or use as static resource
4. [ ] Consider integration with Pile of Law for additional context

---

## 9. Sources and References

### GitHub Repositories
- [awesome-legal-data](https://github.com/openlegaldata/awesome-legal-data) - Curated list
- [PileOfLaw](https://github.com/Breakend/PileOfLaw) - Dataset code
- [statedecoded](https://github.com/statedecoded/statedecoded) - Framework
- [us-statutes](https://github.com/openstatute/us-statutes) - JSON statutes

### Datasets
- [Pile of Law (Hugging Face)](https://huggingface.co/datasets/pile-of-law/pile-of-law)
- [Harvard CAP](https://case.law/)
- [CourtListener Bulk Data](https://www.courtlistener.com/help/api/bulk-data/)

### Official Sources
- [Delaware Code Online](https://delcode.delaware.gov/)
- [Cornell LII - Delaware](https://www.law.cornell.edu/states/delaware)
- [Justia - Delaware](https://law.justia.com/codes/delaware/)

### Papers
- Henderson et al. "Pile of Law" - [arXiv:2207.00220](https://arxiv.org/abs/2207.00220)

---

*Document created: 2026-01-06*
*For: NDA Analyzer - Halmos Capital*
