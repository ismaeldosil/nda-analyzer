# Expected Analysis Results

> Reference for what the NDA Analyzer should flag in `SAMPLE_NDA_PROJECT_ATLAS.md`

---

## Summary

| Issues Found | Count |
|--------------|-------|
| FLAGS | 5 |
| OK | 1 |
| NOT PRESENT | 1 |

**Expected Recommendation**: **Negotiate** (multiple issues to address)

---

## Detailed Expected Results

### FLAGS (Issues to Address)

| # | Clause | Status | Issue | Section |
|---|--------|--------|-------|---------|
| 1 | **Governing Law** | FLAG | New York instead of Delaware | 10.1 |
| 2 | **Term** | FLAG | 3 years (should be ≤2 years) | 9.1 |
| 3 | **Non-Circumvention** | FLAG | Present (should NOT exist) | 5 |
| 4 | **Return of CI** | FLAG | No retention exception allowed | 6.2 |
| 5 | **PE Acknowledgement** | FLAG | NOT PRESENT (should be added) | - |

### OK (Acceptable)

| # | Clause | Status | Why OK | Section |
|---|--------|--------|--------|---------|
| 3 | **Non-Solicitation** | OK | Has carve-outs for general ads, agencies, and self-initiated contact | 4.2 |

### NOT PRESENT (Missing)

| Clause | Impact |
|--------|--------|
| PE Acknowledgement | Critical for PE buyers - should be added |
| Standstill | Good that it's not present |
| Break-up Fee | Good that it's not present |

---

## Key Quotes for Analysis

### Governing Law (FLAG)
> "This Agreement shall be governed by and construed in accordance with the laws of the State of New York..."

**Issue**: Non-Delaware jurisdiction lacks specialized Chancery Court expertise.

### Term (FLAG)
> "This Agreement shall remain in effect for a period of three (3) years from the Effective Date..."

**Issue**: 3 years exceeds market standard of ≤2 years; extends compliance burden.

### Non-Circumvention (FLAG)
> "The Recipient agrees that it shall not, directly or indirectly, contact, deal with, or otherwise circumvent the Company..."

**Issue**: Creates significant liability risk. See *Goodrich Capital v. Vector Capital* ($3.5M fee).

### Return of CI (FLAG)
> "For the avoidance of doubt, the Recipient shall not retain any copies of Confidential Information for any purpose, including for archival, compliance, or backup purposes."

**Issue**: No retention exception for legal/compliance copies. Problematic for regulated buyers.

### Non-Solicitation (OK)
> "The restrictions in Section 4.1 shall not apply to: (a) general solicitations of employment through advertisements... (b) solicitations conducted by recruiting or search firms..."

**Why OK**: Standard buyer-friendly carve-outs are present.

---

## Suggested Additions

### PE Acknowledgement (Generate)

The analyzer should suggest adding:

```
Private Equity Acknowledgement. Atlas Manufacturing Holdings, Inc. acknowledges
that [BUYER] and its affiliates are engaged in the business of private equity
investing and may invest in entities competitive with the Company. Except for
restrictions on disclosure of Confidential Information, this Agreement shall
not prevent [BUYER] or its affiliates from engaging in any business, entering
into agreements with third parties, or evaluating or investing in any entity,
whether or not competitive with the Company.
```

---

## Demo Talking Points

When showing the analysis:

1. **"Look at the Risk Matrix"** - 5 items flagged, clear visual
2. **"Governing Law"** - Common issue, explain Delaware preference
3. **"Non-Circumvention"** - Cite Goodrich Capital case, $3.5M risk
4. **"PE Acknowledgement"** - Critical for PE firms, auto-generated text
5. **"Non-Solicit is OK"** - Show it's not all negative, balanced analysis
6. **"Modified NDA Output"** - Show the generated document with additions

---

*Reference document for NDA Analyzer demo*
