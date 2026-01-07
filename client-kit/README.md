# NDA Analyzer - Client Kit

> Everything you need to use the M&A NDA Analyzer

---

## Quick Start Options

### Option 1: Instant Access (Recommended)
Use our pre-built ChatGPT GPT:
> **[Link to GPT will be added after creation]**

Just click the link and start analyzing NDAs immediately.

### Option 2: Build Your Own
Follow the setup guide to create your own analyzer.

---

## What's Included

```
client-kit/
├── README.md                 # You are here
├── GPT_CONFIGURATION.md      # How to create the ChatGPT GPT
├── prompts/
│   ├── NDA_ANALYZER_PROMPT_FULL.md   # Full analyzer (26 clauses)
│   └── NDA_ANALYZER_PROMPT_LITE.md   # Quick analyzer (6 clauses)
└── samples/
    ├── SAMPLE_NDA_PROJECT_ATLAS.md   # Test NDA with issues
    └── EXPECTED_ANALYSIS.md          # What the analyzer should find
```

---

## How to Use

### If using the shared GPT link:
1. Click the link
2. Upload or paste your NDA
3. Get instant analysis

### If building your own:
1. Read `GPT_CONFIGURATION.md`
2. Copy the prompt from `prompts/NDA_ANALYZER_PROMPT_FULL.md`
3. Create GPT in ChatGPT (or Project in Claude)
4. Test with `samples/SAMPLE_NDA_PROJECT_ATLAS.md`

---

## Features

- **6 Core Clauses** (LITE) or **26 Clauses** (FULL)
- **Risk Matrix** output with clear FLAGS
- **Auto-generated text** for missing clauses
- **Modified NDA** output with suggested additions
- **Delaware-optimized** with case law references

---

## Sample Analysis

The included sample NDA (`Project Atlas`) contains intentional issues:

| Clause | Expected Result |
|--------|-----------------|
| Governing Law | FLAG - New York (not Delaware) |
| Term | FLAG - 3 years (should be ≤2) |
| Non-Circumvention | FLAG - Present (shouldn't exist) |
| Return of CI | FLAG - No retention allowed |
| PE Acknowledgement | FLAG - Not present |
| Non-Solicitation | OK - Has proper exceptions |

---

## Support

Questions? Contact [your contact info]

---

*NDA Analyzer v2.7 | Buyer (PE) Perspective | Delaware-optimized*
