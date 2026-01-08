# NDA Analyzer Frontend - Planning

> Project planning, WBS, and tickets for the Streamlit frontend

---

## Quick Links

| Document | Description |
|----------|-------------|
| [PROJECT-PLAN.md](PROJECT-PLAN.md) | Main project plan with WBS |
| [TICKET-POLICY.md](TICKET-POLICY.md) | How to create tickets |
| [tickets/](tickets/) | Individual ticket files |
| [assets/](assets/) | REEA brand assets |

---

## Tickets Overview

### Epic 1: Project Setup

| Ticket | Title | Priority | Status |
|--------|-------|----------|--------|
| [NDA-001](tickets/NDA-001-repo-setup.md) | Repository and environment setup | P0 | 🔲 Todo |
| NDA-002 | Project structure and config files | P0 | 🔲 Todo |
| NDA-003 | Copy assets and prompts | P0 | 🔲 Todo |

### Epic 2: REEA Branding

| Ticket | Title | Priority | Status |
|--------|-------|----------|--------|
| [NDA-004](tickets/NDA-004-streamlit-theme.md) | Streamlit theme configuration | P0 | 🔲 Todo |
| NDA-005 | Custom CSS implementation | P1 | 🔲 Todo |
| NDA-006 | Logo and favicon setup | P1 | 🔲 Todo |

### Epic 3: User Interface

| Ticket | Title | Priority | Status |
|--------|-------|----------|--------|
| [NDA-007](tickets/NDA-007-main-layout.md) | Main layout and header | P0 | 🔲 Todo |
| NDA-008 | Sidebar configuration panel | P0 | 🔲 Todo |
| NDA-009 | NDA input components | P0 | 🔲 Todo |
| NDA-010 | Results display and Risk Matrix | P0 | 🔲 Todo |
| NDA-011 | Download and export | P2 | 🔲 Todo |

### Epic 4: LLM Integration

| Ticket | Title | Priority | Status |
|--------|-------|----------|--------|
| NDA-012 | Google Gemini API setup | P0 | 🔲 Todo |
| [NDA-013](tickets/NDA-013-analyzer-module.md) | Analyzer module implementation | P0 | 🔲 Todo |
| NDA-014 | Error handling and rate limits | P1 | 🔲 Todo |

### Epic 5: File Processing

| Ticket | Title | Priority | Status |
|--------|-------|----------|--------|
| NDA-015 | PDF and DOCX extraction | P1 | 🔲 Todo |
| NDA-016 | File validation and limits | P2 | 🔲 Todo |

### Epic 6: Testing & Deployment

| Ticket | Title | Priority | Status |
|--------|-------|----------|--------|
| NDA-017 | Manual testing with sample NDA | P0 | 🔲 Todo |
| [NDA-018](tickets/NDA-018-deployment.md) | Streamlit Cloud deployment | P0 | 🔲 Todo |
| NDA-019 | Documentation and client-kit update | P1 | 🔲 Todo |

---

## Assets

| Asset | Path | Description |
|-------|------|-------------|
| REEA Logo | `assets/reea-global-logo.svg` | Official REEA Global logo |
| REEA Styles | `assets/reea-styles.css` | Full CSS from valence-surface |

---

## Execution Order (Recommended)

```
Phase 1: Foundation (Day 1 - Morning)
├── NDA-001 → NDA-002 → NDA-003
└── NDA-004 → NDA-006

Phase 2: UI (Day 1 - Afternoon)
├── NDA-007 → NDA-008 → NDA-009
└── NDA-005

Phase 3: Core (Day 2 - Morning)
├── NDA-012 → NDA-013
└── NDA-010

Phase 4: Polish (Day 2 - Afternoon)
├── NDA-014 → NDA-015 → NDA-016
└── NDA-011

Phase 5: Ship (Day 2 - End)
├── NDA-017 → NDA-018 → NDA-019
```

---

## Status Legend

| Icon | Status |
|------|--------|
| 🔲 | Todo |
| 🔄 | In Progress |
| ✅ | Done |
| ⏸️ | Blocked |

---

*Planning v1.0 | NDA Analyzer Frontend*
