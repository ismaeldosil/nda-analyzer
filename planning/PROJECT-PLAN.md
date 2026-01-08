# NDA Analyzer Frontend - Project Plan

> Streamlit web application with REEA Global branding

---

## Project Overview

| Field | Value |
|-------|-------|
| **Project** | NDA Analyzer Frontend |
| **Client** | Halmos Capital / REEA Global |
| **Stack** | Python, Streamlit, Google Gemini API |
| **Hosting** | Streamlit Cloud (free tier) |
| **Repo** | `nda-analyzer-frontend` |

---

## Objectives

1. Create a branded web interface for the NDA Analyzer
2. Use REEA Global visual identity (colors, fonts, logo)
3. Integrate with Google Gemini API for NDA analysis
4. Deploy to Streamlit Cloud for instant access
5. Provide professional experience for PE firm clients

---

## Work Breakdown Structure (WBS)

```
NDA-FRONTEND
│
├── 1.0 PROJECT SETUP
│   ├── 1.1 Repository Setup
│   │   ├── 1.1.1 Create GitHub repo
│   │   ├── 1.1.2 Initialize Python project
│   │   ├── 1.1.3 Create .gitignore
│   │   └── 1.1.4 Create README.md
│   │
│   ├── 1.2 Development Environment
│   │   ├── 1.2.1 Create virtual environment
│   │   ├── 1.2.2 Install dependencies
│   │   └── 1.2.3 Create requirements.txt
│   │
│   └── 1.3 Project Structure
│       ├── 1.3.1 Create folder structure
│       ├── 1.3.2 Create config files
│       └── 1.3.3 Copy assets (logo, prompts)
│
├── 2.0 REEA BRANDING
│   ├── 2.1 Streamlit Theme
│   │   ├── 2.1.1 Create .streamlit/config.toml
│   │   └── 2.1.2 Configure REEA colors
│   │
│   ├── 2.2 Custom CSS
│   │   ├── 2.2.1 Create styles module
│   │   ├── 2.2.2 Implement header styles
│   │   ├── 2.2.3 Implement button styles
│   │   ├── 2.2.4 Implement alert/badge styles
│   │   └── 2.2.5 Implement table styles
│   │
│   └── 2.3 Assets
│       ├── 2.3.1 Add REEA logo
│       └── 2.3.2 Configure favicon
│
├── 3.0 USER INTERFACE
│   ├── 3.1 Layout
│   │   ├── 3.1.1 Create main app.py
│   │   ├── 3.1.2 Implement header component
│   │   ├── 3.1.3 Implement sidebar component
│   │   └── 3.1.4 Implement main content area
│   │
│   ├── 3.2 Input Components
│   │   ├── 3.2.1 Text area for NDA paste
│   │   ├── 3.2.2 File uploader (PDF, DOCX, TXT)
│   │   ├── 3.2.3 Tab navigation (Paste/Upload)
│   │   └── 3.2.4 Analyze button
│   │
│   ├── 3.3 Configuration Panel
│   │   ├── 3.3.1 Perspective selector (Buyer/Seller)
│   │   ├── 3.3.2 Strictness selector
│   │   ├── 3.3.3 PE Mode toggle
│   │   └── 3.3.4 Output format selector
│   │
│   └── 3.4 Results Display
│       ├── 3.4.1 Loading/spinner state
│       ├── 3.4.2 Risk Matrix rendering
│       ├── 3.4.3 Clause status badges
│       ├── 3.4.4 Must Address section
│       └── 3.4.5 Download button
│
├── 4.0 LLM INTEGRATION
│   ├── 4.1 API Setup
│   │   ├── 4.1.1 Google AI Studio account
│   │   ├── 4.1.2 Generate API key
│   │   └── 4.1.3 Configure secrets
│   │
│   ├── 4.2 Analyzer Module
│   │   ├── 4.2.1 Create analyzer.py
│   │   ├── 4.2.2 Implement Gemini client
│   │   ├── 4.2.3 Build prompt with parameters
│   │   └── 4.2.4 Parse response
│   │
│   └── 4.3 Error Handling
│       ├── 4.3.1 API error handling
│       ├── 4.3.2 Rate limit handling
│       └── 4.3.3 User-friendly error messages
│
├── 5.0 FILE PROCESSING
│   ├── 5.1 Text Extraction
│   │   ├── 5.1.1 Plain text (.txt)
│   │   ├── 5.1.2 PDF extraction
│   │   └── 5.1.3 DOCX extraction
│   │
│   └── 5.2 Validation
│       ├── 5.2.1 File size limits
│       ├── 5.2.2 File type validation
│       └── 5.2.3 Content validation
│
├── 6.0 TESTING
│   ├── 6.1 Manual Testing
│   │   ├── 6.1.1 Test with sample NDA
│   │   ├── 6.1.2 Test all configurations
│   │   └── 6.1.3 Test error scenarios
│   │
│   └── 6.2 UI Testing
│       ├── 6.2.1 Responsive design
│       ├── 6.2.2 Cross-browser testing
│       └── 6.2.3 Mobile testing
│
└── 7.0 DEPLOYMENT
    ├── 7.1 Streamlit Cloud Setup
    │   ├── 7.1.1 Connect GitHub repo
    │   ├── 7.1.2 Configure secrets
    │   └── 7.1.3 Deploy app
    │
    ├── 7.2 Domain (Optional)
    │   ├── 7.2.1 Configure custom domain
    │   └── 7.2.2 SSL verification
    │
    └── 7.3 Documentation
        ├── 7.3.1 Update README
        ├── 7.3.2 Add usage instructions
        └── 7.3.3 Update client-kit with link
```

---

## Epics & Tickets

### Epic 1: Project Setup (NDA-001 to NDA-003)

| Ticket | Title | Priority | Estimate |
|--------|-------|----------|----------|
| NDA-001 | Repository and environment setup | P0 | 30 min |
| NDA-002 | Project structure and config files | P0 | 30 min |
| NDA-003 | Copy assets and prompts | P0 | 15 min |

### Epic 2: REEA Branding (NDA-004 to NDA-006)

| Ticket | Title | Priority | Estimate |
|--------|-------|----------|----------|
| NDA-004 | Streamlit theme configuration | P0 | 30 min |
| NDA-005 | Custom CSS implementation | P1 | 1.5 hours |
| NDA-006 | Logo and favicon setup | P1 | 15 min |

### Epic 3: User Interface (NDA-007 to NDA-011)

| Ticket | Title | Priority | Estimate |
|--------|-------|----------|----------|
| NDA-007 | Main layout and header | P0 | 45 min |
| NDA-008 | Sidebar configuration panel | P0 | 30 min |
| NDA-009 | NDA input components (paste/upload) | P0 | 45 min |
| NDA-010 | Results display and Risk Matrix | P0 | 1 hour |
| NDA-011 | Download and export functionality | P2 | 30 min |

### Epic 4: LLM Integration (NDA-012 to NDA-014)

| Ticket | Title | Priority | Estimate |
|--------|-------|----------|----------|
| NDA-012 | Google Gemini API setup | P0 | 30 min |
| NDA-013 | Analyzer module implementation | P0 | 1.5 hours |
| NDA-014 | Error handling and rate limits | P1 | 45 min |

### Epic 5: File Processing (NDA-015 to NDA-016)

| Ticket | Title | Priority | Estimate |
|--------|-------|----------|----------|
| NDA-015 | PDF and DOCX text extraction | P1 | 1 hour |
| NDA-016 | File validation and limits | P2 | 30 min |

### Epic 6: Testing & Deployment (NDA-017 to NDA-019)

| Ticket | Title | Priority | Estimate |
|--------|-------|----------|----------|
| NDA-017 | Manual testing with sample NDA | P0 | 30 min |
| NDA-018 | Streamlit Cloud deployment | P0 | 30 min |
| NDA-019 | Documentation and client-kit update | P1 | 30 min |

---

## Timeline Summary

| Phase | Tickets | Total Time |
|-------|---------|------------|
| Setup | NDA-001 to NDA-003 | 1.25 hours |
| Branding | NDA-004 to NDA-006 | 2.25 hours |
| UI | NDA-007 to NDA-011 | 3.5 hours |
| LLM | NDA-012 to NDA-014 | 2.75 hours |
| Files | NDA-015 to NDA-016 | 1.5 hours |
| Deploy | NDA-017 to NDA-019 | 1.5 hours |
| **Total** | **19 tickets** | **~12.75 hours** |

---

## Project Structure

```
nda-analyzer-frontend/
├── .streamlit/
│   └── config.toml              # Streamlit theme (REEA colors)
├── .claude/
│   └── CLAUDE.md                # Project context for Claude
├── src/
│   ├── __init__.py
│   ├── analyzer.py              # LLM integration
│   ├── config.py                # App configuration
│   ├── prompts.py               # NDA Analyzer prompts
│   ├── styles.py                # Custom CSS
│   └── file_processor.py        # PDF/DOCX extraction
├── components/
│   ├── __init__.py
│   ├── header.py                # Header with logo
│   ├── sidebar.py               # Configuration panel
│   ├── uploader.py              # Input components
│   └── results.py               # Results display
├── assets/
│   ├── reea-logo.svg            # REEA logo
│   └── favicon.ico              # Favicon
├── tests/
│   └── test_analyzer.py         # Basic tests
├── app.py                       # Main Streamlit app
├── requirements.txt             # Dependencies
├── .env.example                 # Environment template
├── .gitignore
└── README.md
```

---

## Dependencies

```
# requirements.txt
streamlit>=1.29.0
google-generativeai>=0.3.0
python-dotenv>=1.0.0
PyPDF2>=3.0.0
python-docx>=1.0.0
```

---

## REEA Brand Colors

```python
# From valence-surface styles.css
REEA_COLORS = {
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
```

---

## Risk Matrix

| Risk | Impact | Mitigation |
|------|--------|------------|
| API rate limits | Medium | Implement caching, show user feedback |
| Large NDA files | Low | Set file size limits (5MB) |
| PDF extraction fails | Medium | Fallback to text paste |
| Streamlit downtime | Low | Document fallback (Gemini Gem) |

---

## Success Criteria

- [ ] App loads with REEA branding
- [ ] Can analyze NDA via paste or upload
- [ ] Risk Matrix displays correctly
- [ ] All configurations work (perspective, strictness, etc.)
- [ ] Deployed to Streamlit Cloud
- [ ] Client-kit updated with link

---

## Related Documents

- [FRONTEND_PLAN.md](../docs/FRONTEND_PLAN.md) - Original frontend plan
- [TICKET-POLICY.md](./TICKET-POLICY.md) - Ticket creation guidelines
- [tickets/](./tickets/) - Individual ticket files

---

*Project Plan v1.0 | NDA Analyzer Frontend*
