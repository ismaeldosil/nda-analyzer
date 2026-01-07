# NDA Analyzer - Reference Guide

> Prompt versions, configuration parameters, and technical reference

---

## Prompt Versions

### Which Version to Use?

| Scenario | Recommended Version | File |
|----------|---------------------|------|
| **Most common use** | FULL (Standard) | `prompts/compressed/NDA_ANALYZER_PROMPT_FULL.md` |
| High-stakes deal | FULL (Standard) | `prompts/compressed/NDA_ANALYZER_PROMPT_FULL.md` |
| Quick check before call | LITE (Standard) | `prompts/compressed/NDA_ANALYZER_PROMPT_LITE.md` |
| LLM with very limited context | LITE (Standard) | `prompts/compressed/NDA_ANALYZER_PROMPT_LITE.md` |
| Only care about 6 core issues | LITE (Standard) | `prompts/compressed/NDA_ANALYZER_PROMPT_LITE.md` |
| Need negotiation talking points | FULL EXTENDED | `prompts/extended/NDA_ANALYZER_PROMPT_FULL.md` |
| Learning the framework | FULL EXTENDED | `prompts/extended/NDA_ANALYZER_PROMPT_FULL.md` |
| API with unlimited context | FULL EXTENDED | `prompts/extended/NDA_ANALYZER_PROMPT_FULL.md` |

> **Recommendation**: Start with Standard versions. Use Extended only if you need the additional documentation or have unlimited context.

### Standard (Token-Optimized) — Use These by Default

| Version | File | Lines | Use Case |
|---------|------|-------|----------|
| **FULL** | `prompts/compressed/NDA_ANALYZER_PROMPT_FULL.md` | ~444 | Comprehensive analysis, all 26 clauses |
| **LITE** | `prompts/compressed/NDA_ANALYZER_PROMPT_LITE.md` | ~131 | Quick review, 6 core clauses only |

### Extended (Complete Documentation)

| Version | File | Lines | Use Case |
|---------|------|-------|----------|
| **FULL EXTENDED** | `prompts/extended/NDA_ANALYZER_PROMPT_FULL.md` | ~2107 | Full documentation, examples, negotiation positions |
| **LITE EXTENDED** | `prompts/extended/NDA_ANALYZER_PROMPT_LITE.md` | ~275 | Complete LITE with detailed explanations |

### Token Reduction Achieved

| Version | Original | Compressed | Reduction |
|---------|----------|------------|-----------|
| FULL | 2107 lines | 444 lines | **79%** |
| LITE | 275 lines | 131 lines | **52%** |

> **Note**: Standard versions maintain full semantic power. Extended versions include additional examples, negotiation talking points, and verbose explanations.

### Standard vs Extended Comparison

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

## Configuration Parameters

Customize your analysis by specifying parameters:

| Parameter | Options | Default | Description |
|-----------|---------|---------|-------------|
| `PERSPECTIVE` | Buyer / Seller | Buyer | Analysis viewpoint |
| `STRICTNESS` | Strict / Standard / Lenient | Standard | Flagging aggressiveness |
| `OUTPUT_FORMAT` | matrix / summary / full / extended / complete | matrix | Report detail level |
| `TRANSACTION_TYPE` | M&A / JV / Strategic / Licensing / Minority / Due Diligence | M&A | Transaction context |
| `PE_MODE` | Yes / No | Yes | PE-specific analysis |

### Output Format Hierarchy (NEW in v2.7)

| Format | Content | Use Case |
|--------|---------|----------|
| **matrix** | Risk Matrix tables ONLY | Quick risk overview (DEFAULT) |
| **summary** | Matrix + CRITICAL/HIGH findings | Deal team review |
| **full** | Matrix + All findings + Recommendations | Negotiation prep |
| **extended** | Full + Redline templates | Markup drafting |
| **complete** | Extended + Legal sources + Cross-refs | Legal review |

### Strictness Levels

| Level | Behavior |
|-------|----------|
| **Lenient** | Only flag clearly unusual terms. Accept common one-sided provisions. |
| **Standard** | Flag deviations from market practice and asymmetric risks. Typical review. |
| **Strict** | Flag even market-standard terms that create leverage or exposure. For high-stakes deals. |

### Transaction Type

| Type | Severity Adjustment |
|------|---------------------|
| **M&A** | Standard (no adjustment) |
| **JV** | Reduce standstill/hostile risks by 1 level |
| **Strategic** | Reduce standstill/hostile risks by 1 level |
| **Licensing** | Reduce standstill/hostile risks by 1 level |
| **Minority** | Reduce standstill/hostile risks by 1 level |
| **Due Diligence** | Reduce standstill/hostile risks by 1 level |

---

## API Integration

For programmatic use, parameters can be passed as JSON:

```json
{
  "perspective": "Buyer",
  "strictness": "Standard",
  "output_format": "matrix",
  "transaction_type": "M&A",
  "pe_mode": true
}
```

### Example API Prompt Structure
```
System: [Content of prompt file]

User: Analyze this NDA with parameters: {"perspective": "Seller", "output_format": "full"}

[NDA content]
```

---

## Best Practices

1. **Start with matrix output** for quick risk overview
2. **Use summary** when you need to see critical issues
3. **Use full** for detailed negotiation prep
4. **Use extended** when preparing markup/redlines
5. **Use complete** for comprehensive legal review
6. **Always specify perspective** if not default buyer
7. **Use Strict mode** for high-stakes deals
8. **Test with known NDAs** first to calibrate expectations

---

## Testing the Analyzer

If you don't have an NDA to test with:

```
Generate a sample M&A NDA with these characteristics:
- 3-year term (should be flagged)
- Non-circumvention clause (should be flagged)
- No PE Acknowledgement (should be flagged as NOT PRESENT)
- Delaware governing law (should be OK)
- Standard non-solicit with exceptions (should be OK)
- Use clause limited to "transaction between the parties" (should be flagged - backdoor standstill)

Then analyze it using the NDA Analyzer framework.
```

---

## File Structure

```
client-halmos-nda-analyzer-docs/
├── prompts/
│   ├── compressed/
│   │   ├── NDA_ANALYZER_PROMPT_FULL.md   # Standard FULL (use this)
│   │   └── NDA_ANALYZER_PROMPT_LITE.md   # Standard LITE (use this)
│   └── extended/
│       ├── NDA_ANALYZER_PROMPT_FULL.md   # Extended FULL (reference)
│       └── NDA_ANALYZER_PROMPT_LITE.md   # Extended LITE (reference)
└── docs/
    ├── USAGE_GUIDE.md                    # How to use with LLMs
    ├── usage_guide.html                  # HTML version with styling
    ├── REFERENCE.md                      # This file
    └── CHANGELOG.md                      # Version history
```

---

*See CHANGELOG.md for version history and clauses analyzed.*
