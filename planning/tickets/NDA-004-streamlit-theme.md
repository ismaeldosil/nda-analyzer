# [NDA-004] Streamlit Theme Configuration

## Descripción

Configure Streamlit's built-in theming system to use REEA Global brand colors. This ensures the app has consistent branding from the framework level before custom CSS is added.

## Archivos Afectados

| Archivo | Acción | Descripción |
|---------|--------|-------------|
| `.streamlit/config.toml` | Create | Streamlit configuration with REEA colors |
| `src/config.py` | Create | Python config with color constants |

## Contexto Técnico

REEA Brand Colors (from valence-surface styles.css):
- Primary Orange: `#fb511f`
- Black: `#000000`
- White: `#ffffff`
- Light Gray: `#f4f4f4`
- Dark Gray: `#353637`

Font: Roboto (Google Fonts)

## Solución Propuesta

### 1. Create .streamlit/config.toml

```toml
[theme]
# REEA Global Brand Colors
primaryColor = "#fb511f"
backgroundColor = "#ffffff"
secondaryBackgroundColor = "#f4f4f4"
textColor = "#353637"
font = "sans serif"

[server]
headless = true
port = 8501
enableCORS = false

[browser]
gatherUsageStats = false
```

### 2. Create src/config.py

```python
"""
REEA Global Brand Configuration
Based on: valence-surface/site/common/styles.css
"""

# Brand Colors
COLORS = {
    # Primary
    "primary_orange": "#fb511f",
    "secondary_orange": "#e95d34",
    "accent_orange": "#fc5120",

    # Neutrals
    "black": "#000000",
    "white": "#ffffff",
    "light_gray": "#f4f4f4",
    "dark_gray": "#353637",
    "accent_gray": "#707070",
    "border_gray": "#e0e0e0",

    # Semantic
    "success": "#2ecc71",
    "warning": "#f39c12",
    "danger": "#e74c3c",
    "info": "#3498db",
}

# Typography
FONTS = {
    "primary": "'Roboto', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif",
    "mono": "'Monaco', 'Menlo', 'Courier New', monospace",
}

# Spacing
RADIUS = {
    "sm": "8px",
    "md": "16px",
    "lg": "24px",
    "xl": "30px",
}

# App Settings
APP_CONFIG = {
    "title": "NDA Analyzer",
    "subtitle": "Powered by REEA Global",
    "page_icon": "📄",
    "layout": "wide",
}
```

## Antes y Después

### Antes
Default Streamlit theme (blue/white)

### Después
REEA branded theme (orange/black/white)

## Criterios de Aceptación

- [ ] `.streamlit/config.toml` created with REEA colors
- [ ] `src/config.py` created with all brand constants
- [ ] App loads with orange primary color
- [ ] Background is white, secondary is light gray
- [ ] Text color is dark gray
- [ ] No Streamlit default blue visible

## Dependencias

- **Depende de:** NDA-001 (repo setup)
- **Bloquea:** NDA-005 (custom CSS)

## Metadata

- **Priority:** P0
- **Epic:** 2.0 - REEA Branding
- **Estimate:** 30 minutes
- **Labels:** `branding`, `P0-critical`, `epic-branding`
