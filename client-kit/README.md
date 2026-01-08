# NDA Analyzer - Client Kit

> Everything you need to use the M&A NDA Analyzer

---

## Quick Start Options

### Option 1: Instant Access - Gemini Gem (Recommended)

Use our pre-built NDA Analyzer on Google Gemini:

> **[NDA Analyzer Gem](https://gemini.google.com/gem/1eZK-8lANbx0-i_cvSbSbVyfsNyVj3n8u?usp=sharing)**

**Requirements**: Google account (free)

Just click the link, sign in with Google, and start analyzing NDAs immediately.

### Option 2: Build Your Own

Follow the setup guide in `SETUP_GUIDE.md` to create your own analyzer using:
- **Google Gemini** (free) - Create a Gem
- **ChatGPT** (requires Plus subscription - $20/month) - Create a GPT
- **Claude** (requires Pro for sharing) - Create a Project

---

## What's Included

```
client-kit/
├── README.md                 # You are here
├── SETUP_GUIDE.md            # How to create your own analyzer
├── prompts/
│   ├── NDA_ANALYZER_PROMPT_FULL.md   # Full analyzer (26 clauses)
│   └── NDA_ANALYZER_PROMPT_LITE.md   # Quick analyzer (6 clauses)
└── samples/
    ├── SAMPLE_NDA_PROJECT_ATLAS.md   # Test NDA with issues
    └── EXPECTED_ANALYSIS.md          # What the analyzer should find
```

---

## How to Use

### If using the Gemini Gem (Recommended):
1. Click the [Gem link](https://gemini.google.com/gem/1eZK-8lANbx0-i_cvSbSbVyfsNyVj3n8u?usp=sharing)
2. Sign in with your Google account
3. Upload or paste your NDA
4. Get instant analysis

### If building your own:
1. Read `SETUP_GUIDE.md` for step-by-step instructions
2. Copy the prompt from `prompts/NDA_ANALYZER_PROMPT_FULL.md`
3. Create a Gem (Gemini), GPT (ChatGPT Plus), or Project (Claude)
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
