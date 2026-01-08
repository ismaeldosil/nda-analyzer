# NDA Analyzer - Streamlit Frontend Plan

> Plan para crear un frontend con branding REEA usando Streamlit

---

## Overview

**Objetivo**: Crear una app web branded que wrappee el NDA Analyzer
**Stack**: Python + Streamlit
**Hosting**: Streamlit Cloud (gratis) o Hugging Face Spaces
**LLM**: Google Gemini API (tiene free tier generoso)

---

## REEA Brand Assets

### Colores (extraídos del logo)

```python
REEA_COLORS = {
    "primary": "#fb511f",      # Naranja/rojo REEA
    "primary_dark": "#e04518", # Hover state
    "white": "#ffffff",
    "black": "#1a1a1a",
    "gray_light": "#f5f5f5",
    "gray": "#6b7280",
    "success": "#10b981",      # Verde para OK
    "warning": "#f59e0b",      # Amarillo para FLAG
    "error": "#ef4444",        # Rojo para CRITICAL
}
```

### Logo
```
/Users/admin/Projects/REEA Global/documentation/reea-global-logo.svg
```

### Fonts (sugeridas)
- **Headlines**: Inter, Poppins, o system-ui
- **Body**: Inter, -apple-system, sans-serif

---

## Arquitectura

```
┌─────────────────────────────────────────────┐
│              Streamlit App                   │
│  ┌─────────────────────────────────────┐    │
│  │         Header (Logo REEA)          │    │
│  ├─────────────────────────────────────┤    │
│  │      Sidebar (Configuración)        │    │
│  │  - Perspective: Buyer/Seller        │    │
│  │  - Strictness: Standard/Strict      │    │
│  │  - Output Format                    │    │
│  ├─────────────────────────────────────┤    │
│  │         Main Content                │    │
│  │  - Text area / File upload          │    │
│  │  - Analyze button                   │    │
│  │  - Results (Risk Matrix)            │    │
│  └─────────────────────────────────────┘    │
└──────────────────┬──────────────────────────┘
                   │
                   ▼
         ┌─────────────────┐
         │  Google Gemini  │
         │      API        │
         └─────────────────┘
```

---

## Estructura de Archivos

```
nda-analyzer-streamlit/
├── .streamlit/
│   └── config.toml           # Configuración Streamlit (theme)
├── app.py                    # App principal
├── config.py                 # Configuración (colores, settings)
├── prompts.py                # Prompts del analyzer
├── analyzer.py               # Lógica de análisis (llamadas a LLM)
├── components/
│   ├── __init__.py
│   ├── header.py             # Header con logo
│   ├── sidebar.py            # Sidebar de configuración
│   ├── uploader.py           # Upload/paste NDA
│   └── results.py            # Mostrar resultados
├── assets/
│   └── reea-logo.svg         # Logo REEA
├── requirements.txt          # Dependencias
├── .env.example              # Template para API keys
└── README.md                 # Instrucciones
```

---

## Pasos de Implementación

### Fase 1: Setup Inicial (30 min)

| # | Paso | Descripción |
|---|------|-------------|
| 1.1 | Crear repo | `nda-analyzer-streamlit` en GitHub |
| 1.2 | Setup Python | Virtual env, Python 3.11+ |
| 1.3 | Instalar deps | `pip install streamlit google-generativeai python-dotenv` |
| 1.4 | Crear estructura | Carpetas y archivos base |
| 1.5 | Copiar assets | Logo REEA, prompts |

**Comandos**:
```bash
mkdir nda-analyzer-streamlit
cd nda-analyzer-streamlit
python -m venv .venv
source .venv/bin/activate
pip install streamlit google-generativeai python-dotenv
```

**requirements.txt**:
```
streamlit>=1.29.0
google-generativeai>=0.3.0
python-dotenv>=1.0.0
```

---

### Fase 2: Configuración de Estilos REEA (1 hora)

| # | Paso | Descripción |
|---|------|-------------|
| 2.1 | Config Streamlit | `.streamlit/config.toml` con colores REEA |
| 2.2 | CSS personalizado | Estilos adicionales via `st.markdown` |
| 2.3 | Header component | Logo + título |
| 2.4 | Probar estilos | Verificar branding |

**.streamlit/config.toml**:
```toml
[theme]
primaryColor = "#fb511f"
backgroundColor = "#ffffff"
secondaryBackgroundColor = "#f5f5f5"
textColor = "#1a1a1a"
font = "sans serif"

[server]
headless = true
port = 8501
```

**Custom CSS** (en app.py):
```python
st.markdown("""
<style>
    .stApp {
        font-family: 'Inter', -apple-system, sans-serif;
    }
    .main-header {
        background: linear-gradient(135deg, #fb511f 0%, #e04518 100%);
        padding: 1.5rem;
        border-radius: 0.5rem;
        margin-bottom: 2rem;
    }
    .main-header h1 {
        color: white;
        margin: 0;
    }
    .risk-flag {
        background-color: #fef2f2;
        border-left: 4px solid #ef4444;
        padding: 1rem;
        margin: 0.5rem 0;
    }
    .risk-ok {
        background-color: #f0fdf4;
        border-left: 4px solid #10b981;
        padding: 1rem;
        margin: 0.5rem 0;
    }
    .stButton > button {
        background-color: #fb511f;
        color: white;
        border: none;
        padding: 0.75rem 2rem;
        font-weight: 600;
    }
    .stButton > button:hover {
        background-color: #e04518;
    }
</style>
""", unsafe_allow_html=True)
```

---

### Fase 3: UI Principal (2 horas)

| # | Paso | Descripción |
|---|------|-------------|
| 3.1 | Header | Logo REEA + título "NDA Analyzer" |
| 3.2 | Sidebar | Configuración (perspective, strictness, etc.) |
| 3.3 | Input area | Text area + file uploader |
| 3.4 | Analyze button | Botón principal |
| 3.5 | Results area | Placeholder para resultados |

**app.py básico**:
```python
import streamlit as st
from config import REEA_COLORS

# Page config
st.set_page_config(
    page_title="REEA NDA Analyzer",
    page_icon="📄",
    layout="wide"
)

# Custom CSS
st.markdown(CUSTOM_CSS, unsafe_allow_html=True)

# Header
col1, col2 = st.columns([1, 4])
with col1:
    st.image("assets/reea-logo.svg", width=80)
with col2:
    st.title("M&A NDA Analyzer")
    st.caption("Powered by REEA Global")

# Sidebar
with st.sidebar:
    st.header("Configuration")
    perspective = st.selectbox("Perspective", ["Buyer", "Seller"])
    strictness = st.selectbox("Strictness", ["Standard", "Strict", "Lenient"])
    pe_mode = st.checkbox("PE Mode", value=True)

# Main content
st.header("Upload NDA")

tab1, tab2 = st.tabs(["Paste Text", "Upload File"])

with tab1:
    nda_text = st.text_area("Paste your NDA here", height=300)

with tab2:
    uploaded_file = st.file_uploader("Upload NDA", type=["txt", "pdf", "docx"])
    if uploaded_file:
        nda_text = uploaded_file.read().decode()

# Analyze button
if st.button("Analyze NDA", type="primary"):
    if nda_text:
        with st.spinner("Analyzing..."):
            result = analyze_nda(nda_text, perspective, strictness, pe_mode)
            st.markdown(result)
    else:
        st.warning("Please paste or upload an NDA first")
```

---

### Fase 4: Integración LLM (1.5 horas)

| # | Paso | Descripción |
|---|------|-------------|
| 4.1 | Setup API key | Google AI Studio → Get API key |
| 4.2 | Crear analyzer.py | Función que llama a Gemini |
| 4.3 | Integrar prompt | Usar NDA_ANALYZER_PROMPT |
| 4.4 | Parsear respuesta | Formatear Risk Matrix |
| 4.5 | Error handling | Manejo de errores API |

**analyzer.py**:
```python
import google.generativeai as genai
from prompts import NDA_ANALYZER_PROMPT

def analyze_nda(nda_text: str, perspective: str, strictness: str, pe_mode: bool) -> str:
    """Analyze NDA using Google Gemini API"""

    genai.configure(api_key=st.secrets["GOOGLE_API_KEY"])
    model = genai.GenerativeModel('gemini-pro')

    # Build prompt with parameters
    params = f"""
    PERSPECTIVE={perspective}
    STRICTNESS={strictness}
    PE_MODE={'Yes' if pe_mode else 'No'}
    OUTPUT_FORMAT=matrix
    """

    full_prompt = f"""
    {NDA_ANALYZER_PROMPT}

    Parameters: {params}

    Analyze this NDA:

    {nda_text}
    """

    response = model.generate_content(full_prompt)
    return response.text
```

**Obtener API Key**:
1. Ir a https://aistudio.google.com/
2. Click "Get API Key"
3. Crear nueva key
4. Guardar en `.env` o Streamlit Secrets

---

### Fase 5: Formateo de Resultados (1 hora)

| # | Paso | Descripción |
|---|------|-------------|
| 5.1 | Parsear markdown | Extraer Risk Matrix |
| 5.2 | Colorear FLAGS | Rojo para FLAG, verde para OK |
| 5.3 | Mostrar tabla | st.dataframe o HTML table |
| 5.4 | Sección "Must Address" | Destacar items críticos |
| 5.5 | Download button | Descargar análisis como PDF/MD |

**results.py**:
```python
def display_results(analysis: str):
    """Display formatted analysis results"""

    # Show raw markdown
    st.markdown(analysis)

    # Download button
    st.download_button(
        label="Download Analysis",
        data=analysis,
        file_name="nda_analysis.md",
        mime="text/markdown"
    )
```

---

### Fase 6: Deploy (30 min)

| # | Paso | Descripción |
|---|------|-------------|
| 6.1 | Push a GitHub | Subir código |
| 6.2 | Conectar Streamlit Cloud | streamlit.io/cloud |
| 6.3 | Configurar secrets | API key en Streamlit Secrets |
| 6.4 | Deploy | Click deploy |
| 6.5 | Custom domain (opcional) | nda.reea.com |

**Streamlit Cloud Deploy**:
1. Ir a https://streamlit.io/cloud
2. Connect GitHub repo
3. Select `app.py` as main file
4. Add secrets:
   ```toml
   GOOGLE_API_KEY = "your-api-key-here"
   ```
5. Click Deploy

---

## Estimación de Tiempo

| Fase | Tiempo | Acumulado |
|------|--------|-----------|
| 1. Setup Inicial | 30 min | 30 min |
| 2. Estilos REEA | 1 hora | 1.5 horas |
| 3. UI Principal | 2 horas | 3.5 horas |
| 4. Integración LLM | 1.5 horas | 5 horas |
| 5. Formateo Results | 1 hora | 6 horas |
| 6. Deploy | 30 min | **6.5 horas** |

**Total estimado**: ~6-7 horas de desarrollo

---

## Costos

| Item | Costo |
|------|-------|
| Streamlit Cloud | Gratis (tier básico) |
| Google Gemini API | Gratis (límites generosos) |
| Dominio custom (opcional) | ~$12/año |

**Límites gratis de Gemini**:
- 60 requests/minuto
- 1 millón tokens/día
- Suficiente para ~500+ análisis/día

---

## Próximos Pasos

1. [ ] Crear repo `nda-analyzer-streamlit`
2. [ ] Obtener Google API key
3. [ ] Implementar Fase 1 (setup)
4. [ ] Implementar Fase 2 (estilos)
5. [ ] Implementar Fase 3 (UI)
6. [ ] Implementar Fase 4 (LLM)
7. [ ] Implementar Fase 5 (results)
8. [ ] Deploy a Streamlit Cloud
9. [ ] Probar con sample NDA
10. [ ] Compartir link

---

## Alternativas de Hosting

| Plataforma | Pros | Cons |
|------------|------|------|
| **Streamlit Cloud** | Gratis, fácil, SSL incluido | Branding Streamlit visible |
| **Hugging Face Spaces** | Gratis, sin branding | Menos customización |
| **Railway** | Custom domain, profesional | $5/mes |
| **Vercel** | Rápido, profesional | Requiere adapter |

---

## Mockup UI

```
┌────────────────────────────────────────────────────────────┐
│  [REEA Logo]   M&A NDA Analyzer                            │
│                Powered by REEA Global                      │
├──────────────┬─────────────────────────────────────────────┤
│              │                                             │
│ Configuration│  Upload NDA                                 │
│              │  ┌─────────────────────────────────────┐   │
│ Perspective  │  │  [Paste Text]  [Upload File]        │   │
│ [Buyer    ▼] │  │                                     │   │
│              │  │  Paste your NDA here...             │   │
│ Strictness   │  │                                     │   │
│ [Standard ▼] │  │                                     │   │
│              │  │                                     │   │
│ ☑ PE Mode    │  └─────────────────────────────────────┘   │
│              │                                             │
│              │  [        Analyze NDA        ]              │
│              │                                             │
│              │  ─────────────────────────────────────────  │
│              │                                             │
│              │  # NDA RISK MATRIX                          │
│              │                                             │
│              │  **Document**: Sample NDA                   │
│              │  **Recommended Action**: Negotiate          │
│              │                                             │
│              │  ## [!] MUST ADDRESS                        │
│              │  • Term: 3 years → negotiate to ≤2         │
│              │  • PE Ack: Add clause                       │
│              │                                             │
│              │  | Clause | Status | Note |                │
│              │  |--------|--------|------|                │
│              │  | Gov Law | OK | Delaware |               │
│              │  | Term | FLAG | 3 years |                 │
│              │                                             │
└──────────────┴─────────────────────────────────────────────┘
```

---

*Plan v1.0 | NDA Analyzer Streamlit Frontend*
