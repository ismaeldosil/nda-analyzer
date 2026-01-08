# [NDA-001] Repository and Environment Setup

## Descripción

Create the GitHub repository and initialize the Python development environment for the NDA Analyzer Frontend project. This is the foundational setup that all other work depends on.

## Archivos Afectados

| Archivo | Acción | Descripción |
|---------|--------|-------------|
| `README.md` | Create | Project overview and setup instructions |
| `.gitignore` | Create | Python + Streamlit ignores |
| `requirements.txt` | Create | Python dependencies |
| `.env.example` | Create | Environment variables template |

## Contexto Técnico

- Repository: `nda-analyzer-frontend`
- Python version: 3.11+
- Main framework: Streamlit
- LLM: Google Gemini API

## Solución Propuesta

### 1. Create GitHub Repository

```bash
# On GitHub: Create new repo "nda-analyzer-frontend"
# Clone locally
git clone git@github.com:REEA-Global-LLC/nda-analyzer-frontend.git
cd nda-analyzer-frontend
```

### 2. Initialize Python Environment

```bash
# Create virtual environment
python -m venv .venv
source .venv/bin/activate  # macOS/Linux

# Install dependencies
pip install streamlit google-generativeai python-dotenv PyPDF2 python-docx
pip freeze > requirements.txt
```

### 3. Create .gitignore

```gitignore
# Python
__pycache__/
*.py[cod]
*$py.class
.venv/
venv/
env/

# Environment
.env
.env.local

# Streamlit
.streamlit/secrets.toml

# IDE
.idea/
.vscode/
*.swp

# OS
.DS_Store
Thumbs.db
```

### 4. Create .env.example

```env
# Google Gemini API
GOOGLE_API_KEY=your-api-key-here

# Optional: Custom settings
STREAMLIT_SERVER_PORT=8501
```

### 5. Create Initial README.md

```markdown
# NDA Analyzer Frontend

> REEA Global branded web interface for M&A NDA analysis

## Setup

1. Clone repository
2. Create virtual environment: `python -m venv .venv`
3. Activate: `source .venv/bin/activate`
4. Install dependencies: `pip install -r requirements.txt`
5. Copy `.env.example` to `.env` and add your API key
6. Run: `streamlit run app.py`

## Stack

- Python 3.11+
- Streamlit
- Google Gemini API
```

## Criterios de Aceptación

- [ ] GitHub repo created at `REEA-Global-LLC/nda-analyzer-frontend`
- [ ] Virtual environment created and working
- [ ] All dependencies installed without errors
- [ ] `.gitignore` properly ignores sensitive files
- [ ] `.env.example` documents required environment variables
- [ ] `README.md` has basic setup instructions
- [ ] Initial commit pushed to repo

## Dependencias

- **Depende de:** Ninguno (primer ticket)
- **Bloquea:** NDA-002, NDA-003

## Metadata

- **Priority:** P0
- **Epic:** 1.0 - Project Setup
- **Estimate:** 30 minutes
- **Labels:** `setup`, `P0-critical`, `epic-setup`
