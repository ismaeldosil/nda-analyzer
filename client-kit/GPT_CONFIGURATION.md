# ChatGPT GPT Configuration

> Use this to create a public ChatGPT GPT for instant NDA analysis

---

## How to Create the GPT

1. Go to [chat.openai.com](https://chat.openai.com)
2. Click your profile → **My GPTs** → **Create a GPT**
3. Click **Configure** tab
4. Fill in the fields below
5. Click **Save** → Choose **"Everyone"** for public access
6. Copy the share link

---

## GPT Configuration

### Name
```
M&A NDA Analyzer
```

### Description
```
Analyzes M&A NDAs from a Buyer (PE) perspective. Identifies risks, flags issues, and suggests improvements. Delaware-optimized with anti-hallucination guardrails.
```

### Instructions

> Copy the entire content from: `prompts/compressed/NDA_ANALYZER_PROMPT_FULL.md`
>
> Or for a lighter version: `prompts/compressed/NDA_ANALYZER_PROMPT_LITE.md`

### Conversation Starters

```
Analyze this NDA
```

```
Analyze this NDA from the Seller's perspective
```

```
What are the key risks in this NDA?
```

```
Generate a PE Acknowledgement clause for [Company Name]
```

### Capabilities

| Setting | Value |
|---------|-------|
| Web Browsing | OFF |
| DALL-E Image Generation | OFF |
| Code Interpreter | OFF |

### Knowledge Files (Optional)

Upload these for reference:
- `samples/SAMPLE_NDA_PROJECT_ATLAS.md` - Demo NDA for testing

---

## After Creating

1. **Test it** with the sample NDA
2. **Copy the share link** (looks like: `https://chat.openai.com/g/g-xxxxx`)
3. **Share with clients** - they can use immediately with their ChatGPT account

---

## Alternative: Claude Project

If using Claude instead:

1. Go to [claude.ai](https://claude.ai)
2. Create new **Project**
3. Paste prompt into **Project Instructions**
4. Upload sample NDA to project
5. Share project (requires Claude Pro for sharing)

---

*Configuration for NDA Analyzer v2.7*
