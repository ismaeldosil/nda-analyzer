# NDA Analyzer - Setup Guide

> How to create your own NDA Analyzer on different platforms

---

## Live Version Available

A working version is already available here:

> **[NDA Analyzer Gem](https://gemini.google.com/gem/1eZK-8lANbx0-i_cvSbSbVyfsNyVj3n8u?usp=sharing)**

If you want to create your own version, follow the instructions below.

---

## Platform Comparison

| Platform | Cost | Sharing | Recommended |
|----------|------|---------|-------------|
| **Google Gemini** | Free | Link sharing (requires Google account) | Yes |
| **ChatGPT** | Plus required ($20/mo) | Public link | If you have Plus |
| **Claude** | Pro required for sharing | Limited | No |

---

## Option 1: Google Gemini Gem (Recommended)

### Requirements
- Google account (free)

### Steps

1. **Go to Google AI Studio**
   - Visit [aistudio.google.com](https://aistudio.google.com) or [gemini.google.com](https://gemini.google.com)

2. **Create a New Gem**
   - Click on "Gems" or "Create Gem"
   - Give it a name: `M&A NDA Analyzer`

3. **Add Instructions**
   - Copy the entire content from: `prompts/NDA_ANALYZER_PROMPT_FULL.md`
   - Paste into the Gem instructions

4. **Configure Settings**
   - Description: `Analyzes M&A NDAs from a Buyer (PE) perspective. Identifies risks and suggests improvements.`

5. **Save and Share**
   - Save the Gem
   - Click "Share" to get a link
   - Share link with clients

### Testing
- Use `samples/SAMPLE_NDA_PROJECT_ATLAS.md` to test
- Check results against `samples/EXPECTED_ANALYSIS.md`

---

## Option 2: ChatGPT GPT

### Requirements
- **ChatGPT Plus subscription ($20/month)** - Required to create GPTs
- Note: Users can access your shared GPT with a free account

### Steps

1. **Go to ChatGPT**
   - Visit [chat.openai.com](https://chat.openai.com)
   - Must be logged into Plus account

2. **Create a GPT**
   - Click your profile → **My GPTs** → **Create a GPT**
   - Click **Configure** tab

3. **Fill in Configuration**

   **Name:**
   ```
   M&A NDA Analyzer
   ```

   **Description:**
   ```
   Analyzes M&A NDAs from a Buyer (PE) perspective. Identifies risks, flags issues, and suggests improvements. Delaware-optimized with anti-hallucination guardrails.
   ```

   **Instructions:**
   - Copy entire content from: `prompts/NDA_ANALYZER_PROMPT_FULL.md`

   **Conversation Starters:**
   ```
   Analyze this NDA
   ```
   ```
   Analyze this NDA from the Seller's perspective
   ```
   ```
   What are the key risks in this NDA?
   ```

4. **Capabilities** (disable all)
   - Web Browsing: OFF
   - DALL-E: OFF
   - Code Interpreter: OFF

5. **Save and Share**
   - Click **Save** → Choose **"Everyone"** for public access
   - Copy the share link

---

## Option 3: Claude Project

### Requirements
- **Claude Pro** ($20/month) - Required for sharing projects

### Steps

1. **Go to Claude**
   - Visit [claude.ai](https://claude.ai)

2. **Create a Project**
   - Click "Projects" → "New Project"
   - Name: `M&A NDA Analyzer`

3. **Add Project Instructions**
   - Paste content from `prompts/NDA_ANALYZER_PROMPT_FULL.md`

4. **Share** (Pro only)
   - Click share settings to generate link

---

## Option 4: Direct Conversation (Any Platform - Free)

If you don't want to create a Gem/GPT, you can use the analyzer directly:

1. **Open any LLM** (ChatGPT, Gemini, Claude - free tiers work)

2. **First message - Setup:**
   ```
   I'm going to provide you with an NDA analysis framework.

   [Paste entire content of prompts/NDA_ANALYZER_PROMPT_FULL.md]

   Confirm you're ready to analyze.
   ```

3. **Second message - Analyze:**
   ```
   Analyze this NDA:

   [Paste NDA text]
   ```

This works with free accounts but requires pasting the prompt each session.

---

## Testing Your Setup

Use the included sample NDA to verify your setup works:

1. Open `samples/SAMPLE_NDA_PROJECT_ATLAS.md`
2. Paste into your analyzer
3. Compare results with `samples/EXPECTED_ANALYSIS.md`

### Expected Results

| Clause | Expected |
|--------|----------|
| Governing Law | FLAG - New York |
| Term | FLAG - 3 years |
| Non-Circumvention | FLAG - Present |
| Return of CI | FLAG - No retention |
| PE Acknowledgement | FLAG - Not present |
| Non-Solicitation | OK - Has exceptions |

---

*Setup Guide v2.7 | NDA Analyzer*
