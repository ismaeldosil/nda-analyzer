# M&A NDA Analyzer

> LLM-powered system prompts for analyzing Non-Disclosure Agreements in M&A transactions.

## Overview

This repository contains system prompts designed to analyze NDAs from a **Buyer (PE Fund) perspective**, optimized for Delaware law. The prompts can be used with ChatGPT, Claude, Gemini, or any other LLM.

## Quick Start

1. Copy the prompt from `prompts/compressed/NDA_ANALYZER_PROMPT_LITE.md`
2. Paste it into your LLM (ChatGPT, Claude, Gemini)
3. Upload or paste your NDA
4. Get instant risk analysis

## Prompts

### Compressed (Recommended)

| Version | Clauses | Best For |
|---------|---------|----------|
| [FULL](prompts/compressed/NDA_ANALYZER_PROMPT_FULL.md) | 26 | Complete M&A NDA analysis |
| [LITE](prompts/compressed/NDA_ANALYZER_PROMPT_LITE.md) | 6 | Quick reviews, limited context LLMs |

### Extended (Reference)

| Version | Use Case |
|---------|----------|
| [FULL Extended](prompts/extended/NDA_ANALYZER_PROMPT_FULL.md) | Includes negotiation positions, examples |
| [LITE Extended](prompts/extended/NDA_ANALYZER_PROMPT_LITE.md) | Detailed explanations for learning |

## Features

- **Anti-Hallucination**: Marks missing clauses as "NOT PRESENT" instead of assuming
- **Quote-Before-Assess**: Always quotes exact NDA text before classifying
- **Risk Matrix Output**: Clean, actionable risk summary
- **Delaware Optimized**: Baseline expectations for Delaware law
- **PE Mode**: Special handling for Private Equity buyers
- **Suggest Additions**: Auto-generates suggested text for missing clauses
- **Modified NDA Output**: Generates complete NDA with suggested clauses inserted

## Core Clauses Analyzed

| # | Clause | Buyer Ideal |
|---|--------|-------------|
| 1 | Governing Law | Delaware |
| 2 | Term | ≤ 2 years |
| 3 | Non-Solicitation | Has exceptions for general ads + agencies |
| 4 | Non-Circumvention | NOT PRESENT |
| 5 | Return of CI | Allows retention for compliance |
| 6 | PE Acknowledgement | Present |

## Sample Output

```
# NDA RISK MATRIX

**Document**: Project Alpha NDA | **Perspective**: Buyer

**Recommended Action**: Negotiate

## [!] MUST ADDRESS

- **Term**: 3 years too long - negotiate to ≤2 years
- **PE Ack**: Add PE acknowledgement clause

## CORE CLAUSES

| # | Clause | Status | Note |
|---|--------|--------|------|
| 1 | Governing Law | OK | Delaware |
| 2 | Term | [!] FLAG | 3 years |
| 3 | Non-Solicit | OK | Has exceptions |
| 4 | Non-Circumvent | OK | Not present |
| 5 | Return of CI | OK | Retention allowed |
| 6 | PE Ack | [!] FLAG | Not present |
```

## Legal Sources

The analysis references established M&A case law:

| Case | Relevance |
|------|-----------|
| *Martin Marietta v. Vulcan Materials* (Del. Ch. 2012) | Use clauses as backdoor standstills |
| *Goodrich Capital v. Vector Capital* (S.D.N.Y. 2012) | Non-circumvention liability ($3.5M) |
| *Space Data v. Google* (N.D. Cal. 2017) | Residual clause difficulties |

## Documentation

- [Usage Guide](docs/USAGE_GUIDE.md) - How to use with different LLMs
- [Changelog](docs/CHANGELOG.md) - Version history
- [Reference](docs/REFERENCE.md) - Technical specifications

## Version

**v2.7** - Auto-Analyze Release
- Interactive onboarding
- Matrix output as default
- Legal sources in LITE version
- SUGGEST_ADDITIONS with modified NDA generation

## License

MIT

## Disclaimer

This tool is for informational purposes only and does not constitute legal advice. Always consult qualified legal counsel for NDA review in actual transactions.
