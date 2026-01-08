# [NDA-007] Main Layout and Header Component

## Descripción

Create the main application layout including the branded header with REEA logo, subtitle, and the overall page structure. This establishes the visual foundation for all other UI components.

## Archivos Afectados

| Archivo | Acción | Descripción |
|---------|--------|-------------|
| `app.py` | Create | Main Streamlit application |
| `components/__init__.py` | Create | Components package |
| `components/header.py` | Create | Header component with logo |
| `src/styles.py` | Create | Custom CSS styles |

## Contexto Técnico

Layout structure:
```
┌─────────────────────────────────────────────┐
│           HEADER (Logo + Title)             │
├──────────────┬──────────────────────────────┤
│   SIDEBAR    │       MAIN CONTENT           │
│  (Config)    │    (Input + Results)         │
└──────────────┴──────────────────────────────┘
```

## Solución Propuesta

### 1. Create app.py

```python
"""
NDA Analyzer - REEA Global
Main Streamlit Application
"""
import streamlit as st
from src.config import APP_CONFIG, COLORS
from src.styles import get_custom_css
from components.header import render_header
from components.sidebar import render_sidebar

# Page configuration
st.set_page_config(
    page_title=APP_CONFIG["title"],
    page_icon=APP_CONFIG["page_icon"],
    layout=APP_CONFIG["layout"],
    initial_sidebar_state="expanded"
)

# Inject custom CSS
st.markdown(get_custom_css(), unsafe_allow_html=True)

# Render header
render_header()

# Render sidebar and get config
config = render_sidebar()

# Main content area
st.markdown("---")

# Tabs for input
tab1, tab2 = st.tabs(["📝 Paste Text", "📁 Upload File"])

with tab1:
    nda_text = st.text_area(
        "Paste your NDA here",
        height=300,
        placeholder="Paste the full NDA text..."
    )

with tab2:
    uploaded_file = st.file_uploader(
        "Upload NDA document",
        type=["txt", "pdf", "docx"],
        help="Supported formats: TXT, PDF, DOCX (max 5MB)"
    )

# Analyze button
col1, col2, col3 = st.columns([1, 2, 1])
with col2:
    analyze_btn = st.button(
        "🔍 Analyze NDA",
        type="primary",
        use_container_width=True
    )

# Results area (placeholder for NDA-010)
if analyze_btn:
    st.info("Analysis functionality coming in NDA-013")
```

### 2. Create components/header.py

```python
"""
Header Component - REEA Global Branding
"""
import streamlit as st
from src.config import COLORS

def render_header():
    """Render the branded header with logo and title."""

    # Custom header HTML
    header_html = f"""
    <div class="reea-header">
        <div class="header-content">
            <div class="logo-section">
                <img src="app/static/reea-logo.svg" alt="REEA Global" class="logo">
            </div>
            <div class="title-section">
                <h1>M&A NDA Analyzer</h1>
                <p class="subtitle">Powered by REEA Global</p>
            </div>
        </div>
    </div>
    """

    # Alternative using Streamlit columns (if static files don't work)
    col1, col2 = st.columns([1, 5])

    with col1:
        st.image("assets/reea-logo.svg", width=80)

    with col2:
        st.markdown(
            f"""
            <h1 style="color: {COLORS['black']}; margin-bottom: 0;">
                M&A NDA Analyzer
            </h1>
            <p style="color: {COLORS['accent_gray']}; margin-top: 0;">
                Powered by REEA Global
            </p>
            """,
            unsafe_allow_html=True
        )
```

### 3. Create src/styles.py

```python
"""
Custom CSS Styles - REEA Global Brand
Based on: valence-surface/site/common/styles.css
"""
from src.config import COLORS, FONTS, RADIUS

def get_custom_css() -> str:
    """Return custom CSS for REEA branding."""
    return f"""
    <style>
        /* Import Roboto font */
        @import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;600;700;900&display=swap');

        /* Base styles */
        .stApp {{
            font-family: {FONTS['primary']};
        }}

        /* Header styles */
        .reea-header {{
            background: linear-gradient(135deg, {COLORS['black']} 0%, {COLORS['dark_gray']} 100%);
            padding: 2rem;
            border-radius: {RADIUS['xl']};
            margin-bottom: 2rem;
        }}

        .reea-header h1 {{
            color: {COLORS['white']};
            font-weight: 900;
            text-transform: uppercase;
            letter-spacing: 1px;
        }}

        .reea-header .subtitle {{
            color: {COLORS['primary_orange']};
            font-weight: 300;
        }}

        /* Primary button override */
        .stButton > button[kind="primary"] {{
            background-color: {COLORS['primary_orange']};
            border: none;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            padding: 0.75rem 2rem;
            border-radius: {RADIUS['lg']};
        }}

        .stButton > button[kind="primary"]:hover {{
            background-color: {COLORS['secondary_orange']};
        }}

        /* Sidebar styling */
        [data-testid="stSidebar"] {{
            background-color: {COLORS['light_gray']};
        }}

        [data-testid="stSidebar"] h2 {{
            color: {COLORS['black']};
            border-bottom: 4px solid {COLORS['primary_orange']};
            padding-bottom: 0.5rem;
        }}

        /* Alert styles */
        .risk-flag {{
            background-color: rgba(231, 76, 60, 0.12);
            border-left: 5px solid {COLORS['danger']};
            padding: 1rem;
            border-radius: {RADIUS['md']};
            margin: 0.5rem 0;
        }}

        .risk-ok {{
            background-color: rgba(46, 204, 113, 0.12);
            border-left: 5px solid {COLORS['success']};
            padding: 1rem;
            border-radius: {RADIUS['md']};
            margin: 0.5rem 0;
        }}

        /* Badge styles */
        .badge {{
            display: inline-block;
            padding: 0.35rem 0.9rem;
            border-radius: {RADIUS['lg']};
            font-size: 0.75rem;
            font-weight: 700;
            text-transform: uppercase;
        }}

        .badge-flag {{
            background: {COLORS['danger']};
            color: {COLORS['white']};
        }}

        .badge-ok {{
            background: {COLORS['success']};
            color: {COLORS['white']};
        }}

        /* Table styles */
        .dataframe {{
            border-radius: {RADIUS['md']};
            overflow: hidden;
        }}

        .dataframe th {{
            background: {COLORS['black']} !important;
            color: {COLORS['white']} !important;
            font-weight: 600;
            text-transform: uppercase;
        }}
    </style>
    """
```

## Criterios de Aceptación

- [ ] `app.py` runs without errors
- [ ] Header displays with REEA logo and title
- [ ] Sidebar is visible and styled
- [ ] Main content area has tabs for Paste/Upload
- [ ] Analyze button is orange (REEA primary)
- [ ] Overall layout matches mockup
- [ ] Responsive on different screen sizes

## Dependencias

- **Depende de:** NDA-004 (theme), NDA-006 (assets)
- **Bloquea:** NDA-008, NDA-009, NDA-010

## Metadata

- **Priority:** P0
- **Epic:** 3.0 - User Interface
- **Estimate:** 45 minutes
- **Labels:** `ui`, `P0-critical`, `epic-ui`
