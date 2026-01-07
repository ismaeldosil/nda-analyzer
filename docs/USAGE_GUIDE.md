# NDA Analyzer - Usage Guide

> How to use the M&A NDA Analyzer prompt with different LLMs

---

## Using with ChatGPT / GPT-4

### Method 1: Custom Instructions (Recommended for repeated use)

1. **Open Settings**
   - Click your avatar (bottom-left corner)
   - Select "Customize ChatGPT" or "Custom instructions"

2. **Paste the prompt**
   - In the second field ("How would you like ChatGPT to respond?")
   - Paste the entire content of the prompt file
   - Note: If too long, paste from the beginning through "KEYWORD DETECTION REFERENCE"

3. **Save** and start a new conversation

4. **Analyze NDAs**
   ```
   Analyze this NDA:

   [paste NDA text here]
   ```

### Method 2: Direct Conversation (Quick one-time use)

1. **Start a new ChatGPT conversation**

2. **First message** - Setup:
   ```
   I'm going to provide you with an NDA analysis framework, then share an NDA for review.

   [Paste entire prompt content]

   Confirm you're ready to analyze.
   ```

3. **Second message** - Analysis:
   ```
   Analyze this NDA:

   [Paste NDA text or upload PDF]
   ```

### Method 3: File Upload (GPT-4 with attachments)

1. **Attach the NDA** as PDF or DOCX (paperclip icon)

2. **Prompt**:
   ```
   Use this NDA analysis framework:

   [Paste prompt content]

   Analyze the attached document.
   ```

---

## Using with Claude

### Method 1: Project Instructions (Recommended)

1. **Create a new Project** in Claude
2. **Add to Project Instructions**: Paste the prompt content
3. **Upload NDAs** to the project or paste in chat
4. **Prompt**: `Analyze this NDA`

### Method 2: Direct Conversation

1. **Start new conversation**

2. **First message**:
   ```
   Here is my NDA analysis framework:

   [Paste prompt content]

   I'll now share an NDA for analysis.
   ```

3. **Second message**:
   ```
   Please analyze this NDA according to the framework:

   [Paste NDA text]
   ```

### Method 3: File Upload

1. **Attach NDA** (PDF supported)
2. **Prompt**:
   ```
   Using the NDA analysis framework I provided, analyze this attached document.
   ```

---

## Using with Google Gemini

### Method 1: Conversation Context

1. **Start new Gemini chat**

2. **First message**:
   ```
   I need you to analyze NDAs using this framework:

   [Paste prompt content]

   Acknowledge when ready.
   ```

3. **Second message**:
   ```
   Analyze this NDA:

   [Paste NDA text]
   ```

### Method 2: With Google Docs

1. **Upload NDA** to Google Drive
2. **In Gemini**: Reference the document
3. **Prompt**: Include the framework and ask for analysis

---

## Example Prompts

### Basic Usage

```
Analyze this NDA
```

```
Analyze this NDA with PERSPECTIVE=Seller
```

```
Analyze this NDA with OUTPUT_FORMAT=Executive
```

```
Analyze this NDA with STRICTNESS=Strict, PE_MODE=Yes
```

### Natural Language

```
Analyze this NDA from the seller's perspective, being strict about issues
```

```
This is a joint venture NDA, not an M&A deal. Analyze accordingly.
```

### Common Scenarios

**Initial Deal Review:**
```
Analyze this NDA. We're the buyer (PE fund) looking at a potential acquisition.
Focus on any deal-breakers or significant negotiation points.
```

**Quick Risk Check:**
```
Analyze this NDA with OUTPUT_FORMAT=Executive.
Just give me the key risks and whether we should sign as-is.
```

**Preparing Negotiation Points:**
```
Analyze this NDA with INCLUDE_REDLINES=Yes.
I need specific language to propose for any problematic clauses.
```

### Special Features

**Generate PE Acknowledgement:**
```
This NDA is missing PE Acknowledgement. Generate insertion text for "Halmos Capital Partners"
```

**Get Suggested Redlines:**
```
Provide redline suggestions for the flagged issues
```

**AI Restrictions Analysis:**
```
Does this NDA prohibit inputting Confidential Information into AI tools like ChatGPT?
```

---

## Troubleshooting

### "Response is too long / got cut off"
```
Continue the analysis from where you left off
```
Or use:
```
Analyze this NDA with OUTPUT_FORMAT=Summary
```

### "Not following the format"
```
Please follow the exact output format from the NDA analysis framework,
including the Risk Assessment Matrix table
```

### "Assuming clauses exist"
```
Remember the anti-hallucination rule: If a clause is not found, mark it as "NOT PRESENT".
Do not assume market-standard inclusion.
```

### "Need more detail on specific clause"
```
Expand on the Non-Solicit analysis. What exactly does it restrict?
```

---

*For prompt versions, configuration parameters, and technical reference, see REFERENCE.md*
