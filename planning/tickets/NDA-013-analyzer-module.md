# [NDA-013] Analyzer Module Implementation

## Descripción

Implement the core analyzer module that integrates with Google Gemini API to analyze NDAs. This module takes NDA text and configuration parameters, builds the appropriate prompt, calls the LLM, and returns the analysis results.

## Archivos Afectados

| Archivo | Acción | Descripción |
|---------|--------|-------------|
| `src/analyzer.py` | Create | Main analyzer class with Gemini integration |
| `src/prompts.py` | Create | NDA Analyzer prompts (FULL and LITE) |
| `app.py` | Modify | Integrate analyzer with UI |

## Contexto Técnico

- LLM: Google Gemini Pro (gemini-pro model)
- API: google-generativeai Python SDK
- Prompts: From `client-kit/prompts/NDA_ANALYZER_PROMPT_FULL.md`

Parameters to support:
- PERSPECTIVE: Buyer / Seller
- STRICTNESS: Lenient / Standard / Strict
- PE_MODE: Yes / No
- OUTPUT_FORMAT: matrix (default)

## Solución Propuesta

### 1. Create src/prompts.py

```python
"""
NDA Analyzer Prompts
Source: client-kit/prompts/NDA_ANALYZER_PROMPT_FULL.md
"""

NDA_ANALYZER_PROMPT_FULL = """
# M&A NDA Analyzer v2.7

> System prompt for analyzing NDAs in M&A transactions. Delaware-optimized. Buyer/Seller perspectives.

---

## MANDATORY RULES

### Anti-Hallucination
- If clause NOT found → mark "NOT PRESENT"
- Do NOT assume/infer existence
- Do NOT state "likely exists" or "typically included"

### Quote-Before-Assess
Before classifying ANY clause:
1. QUOTE exact language (blockquote)
2. THEN assess

... [Full prompt content from NDA_ANALYZER_PROMPT_FULL.md]
"""

NDA_ANALYZER_PROMPT_LITE = """
# M&A NDA Analyzer - LITE v2.7

> 6 core clauses | Delaware-optimized | Quick review

... [Full prompt content from NDA_ANALYZER_PROMPT_LITE.md]
"""
```

### 2. Create src/analyzer.py

```python
"""
NDA Analyzer - Google Gemini Integration
"""
import streamlit as st
import google.generativeai as genai
from dataclasses import dataclass
from typing import Optional
from src.prompts import NDA_ANALYZER_PROMPT_FULL, NDA_ANALYZER_PROMPT_LITE


@dataclass
class AnalysisConfig:
    """Configuration for NDA analysis."""
    perspective: str = "Buyer"
    strictness: str = "Standard"
    pe_mode: bool = True
    output_format: str = "matrix"
    use_lite: bool = False


class NDAAnalyzer:
    """
    NDA Analyzer using Google Gemini API.

    Usage:
        analyzer = NDAAnalyzer()
        result = analyzer.analyze(nda_text, config)
    """

    def __init__(self):
        """Initialize the analyzer with Gemini API."""
        self._configure_api()
        self.model = genai.GenerativeModel('gemini-pro')

    def _configure_api(self):
        """Configure Google Gemini API with key from secrets."""
        api_key = st.secrets.get("GOOGLE_API_KEY")
        if not api_key:
            raise ValueError("GOOGLE_API_KEY not found in secrets")
        genai.configure(api_key=api_key)

    def _build_prompt(self, nda_text: str, config: AnalysisConfig) -> str:
        """Build the full prompt with system instructions and NDA text."""

        # Select base prompt
        base_prompt = (
            NDA_ANALYZER_PROMPT_LITE if config.use_lite
            else NDA_ANALYZER_PROMPT_FULL
        )

        # Build parameters string
        params = f"""
PERSPECTIVE={config.perspective}
STRICTNESS={config.strictness}
PE_MODE={'Yes' if config.pe_mode else 'No'}
OUTPUT_FORMAT={config.output_format}
"""

        # Combine into full prompt
        full_prompt = f"""
{base_prompt}

---

## ANALYSIS PARAMETERS

{params}

---

## NDA TO ANALYZE

{nda_text}

---

Please analyze this NDA following the framework above.
"""
        return full_prompt

    def analyze(
        self,
        nda_text: str,
        config: Optional[AnalysisConfig] = None
    ) -> str:
        """
        Analyze an NDA and return the risk matrix.

        Args:
            nda_text: The full text of the NDA
            config: Analysis configuration (uses defaults if None)

        Returns:
            Analysis result as markdown string
        """
        if config is None:
            config = AnalysisConfig()

        # Build prompt
        prompt = self._build_prompt(nda_text, config)

        # Call Gemini API
        try:
            response = self.model.generate_content(
                prompt,
                generation_config=genai.GenerationConfig(
                    temperature=0.2,  # Lower for more consistent output
                    max_output_tokens=4096,
                )
            )
            return response.text

        except genai.types.BlockedPromptException:
            return "⚠️ Analysis blocked: The content was flagged by safety filters."

        except Exception as e:
            return f"❌ Error during analysis: {str(e)}"


# Singleton instance for reuse
@st.cache_resource
def get_analyzer() -> NDAAnalyzer:
    """Get cached analyzer instance."""
    return NDAAnalyzer()
```

### 3. Update app.py (integration)

```python
# Add to imports
from src.analyzer import get_analyzer, AnalysisConfig

# In the analyze button handler
if analyze_btn:
    # Get text from paste or upload
    text_to_analyze = nda_text or extract_text(uploaded_file)

    if not text_to_analyze:
        st.warning("Please paste or upload an NDA first")
    else:
        # Build config from sidebar
        config = AnalysisConfig(
            perspective=config["perspective"],
            strictness=config["strictness"],
            pe_mode=config["pe_mode"],
            output_format="matrix"
        )

        # Run analysis
        with st.spinner("🔍 Analyzing NDA..."):
            analyzer = get_analyzer()
            result = analyzer.analyze(text_to_analyze, config)

        # Display results
        st.markdown("---")
        st.markdown("## 📊 Analysis Results")
        st.markdown(result)

        # Download button
        st.download_button(
            label="📥 Download Analysis",
            data=result,
            file_name="nda_analysis.md",
            mime="text/markdown"
        )
```

## Antes y Después

### Antes
```python
# No analysis functionality
if analyze_btn:
    st.info("Analysis functionality coming soon")
```

### Después
```python
# Full Gemini-powered analysis
if analyze_btn:
    with st.spinner("🔍 Analyzing NDA..."):
        analyzer = get_analyzer()
        result = analyzer.analyze(nda_text, config)
    st.markdown(result)
```

## Criterios de Aceptación

- [ ] `NDAAnalyzer` class implemented and working
- [ ] Gemini API integration successful
- [ ] Prompt includes all configuration parameters
- [ ] Analysis returns proper Risk Matrix format
- [ ] Error handling for API failures
- [ ] Results display in Streamlit UI
- [ ] Download button works
- [ ] Test with sample NDA returns expected results

## Dependencias

- **Depende de:** NDA-012 (API setup), NDA-007 (main layout)
- **Bloquea:** NDA-017 (testing)

## Metadata

- **Priority:** P0
- **Epic:** 4.0 - LLM Integration
- **Estimate:** 1.5 hours
- **Labels:** `llm`, `P0-critical`, `epic-llm`, `core`
