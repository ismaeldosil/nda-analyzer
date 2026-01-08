# Harleigh Chatbot - Ticket Creation Policy

## Overview

This document defines the standard format for creating tickets (GitHub Issues) in the Harleigh Chatbot project. All tickets must follow this template to ensure consistency, clarity, and efficient execution by AI agents.

---

## Ticket Template

```markdown
# [HAR-XXX] Ticket Title

## Descripción

[Clear description of what needs to be done and why]

## Subagentes Asignados

| Agente | Rol | Archivo |
|--------|-----|---------|
| `@agent-name` | Lead/Support: What they do | `.claude/agents/category/agent.md` |
| `@agent-name` | Support: What they do | `.claude/agents/category/agent.md` |
| `@code-reviewer` | Review: Verificar calidad | `.claude/agents/qa/code-reviewer.md` |

## Documentación Requerida

| Documento | Propósito |
|-----------|-----------|
| [Document Name](path/to/doc.md) | Why it's needed |
| [CLAUDE.md](../CLAUDE.md) | Project context |

## Archivos Afectados

| Archivo | Acción | Descripción |
|---------|--------|-------------|
| `src/path/to/file.py` | Create/Modify | What changes needed |
| `tests/test_file.py` | Create | Tests to add |

## Contexto Técnico

[Any relevant technical context, existing code, or constraints]

## Solución Propuesta

### 1. [Step 1 Title]
```language
// Code example showing the approach
```

### 2. [Step 2 Title]
```language
// More code examples
```

## Antes y Después

### Antes (Actual)
```language
// Current code or state
```

### Después (Propuesto)
```language
// Proposed code or state
```

## Criterios de Aceptación

- [ ] Criterio específico y verificable 1
- [ ] Criterio específico y verificable 2
- [ ] Tests escritos y pasando
- [ ] Documentación actualizada
- [ ] Code review aprobado
- [ ] Sin errores de lint/type

## Dependencias

- **Depende de:** #issue-number
- **Bloquea:** #issue-number

## Metadata

- **Priority:** P0/P1/P2
- **Epic:** Epic name
- **Phase:** Phase number
- **Labels:** label1, label2
```

---

## Section Details

### 1. Descripción

- Clear, concise description of the task
- Include the **why** not just the **what**
- Reference any related context or decisions

### 2. Subagentes Asignados

Each ticket must specify:
- **Lead Agent:** Primary owner of the task
- **Support Agents:** Contributors with specific expertise
- **Review Agent:** Always include `@code-reviewer`

Available agents:

| Category | Agents |
|----------|--------|
| Backend | `@api-developer`, `@database-engineer`, `@python-developer` |
| AI/RAG | `@rag-engineer`, `@prompt-engineer`, `@llm-integrator`, `@langchain-developer` |
| Frontend | `@react-developer`, `@ui-designer`, `@widget-developer` |
| DevOps | `@devops-engineer`, `@infrastructure-engineer`, `@security-engineer` |
| QA | `@qa-engineer`, `@code-reviewer`, `@performance-tester` |
| Commercial | `@analytics-engineer`, `@shopify-integrator` |

### 3. Documentación Requerida

List all documents the agents should read before starting:

```markdown
| Documento | Propósito |
|-----------|-----------|
| [PROJECT-SPEC.md](../PROJECT-SPEC.md) | Architecture overview |
| [harleigh-system-prompt.md](../.claude/prompts/harleigh-system-prompt.md) | Agent personality |
| [api-developer.md](../.claude/agents/backend/api-developer.md) | Code standards |
```

### 4. Archivos Afectados

Be specific about files:

```markdown
| Archivo | Acción | Descripción |
|---------|--------|-------------|
| `src/rag/retrieval.py` | Modify | Add hybrid search |
| `src/rag/keyword_search.py` | Create | BM25 implementation |
| `tests/test_rag.py` | Modify | Add hybrid search tests |
| `src/config.py` | Modify | Add hybrid search config |
```

### 5. Solución Propuesta

Include code examples showing the approach:

```markdown
### 1. Create hybrid search function

```python
async def hybrid_search(
    query: str,
    vector_weight: float = 0.7,
    keyword_weight: float = 0.3
) -> list[dict]:
    # Vector search
    vector_results = await self.vector_store.query(...)

    # Keyword search
    keyword_results = await self.keyword_search(...)

    # Combine scores
    return self._combine_results(vector_results, keyword_results)
```

### 2. Configure weights

```python
# src/config.py
class Settings:
    hybrid_vector_weight: float = 0.7
    hybrid_keyword_weight: float = 0.3
```
```

### 6. Antes y Después

Show the transformation clearly:

```markdown
### Antes
```python
# Only vector search
results = await self.vector_store.query(embedding)
```

### Después
```python
# Hybrid search
results = await self.hybrid_search(query, vector_weight=0.7)
```
```

### 7. Criterios de Aceptación

Use checkboxes with specific, testable criteria:

```markdown
- [ ] Hybrid search function implemented in `src/rag/retrieval.py`
- [ ] Configurable weights via environment variables
- [ ] Unit tests with >80% coverage
- [ ] Integration test verifying improved relevance
- [ ] Performance: latency increase < 100ms
- [ ] Documentation updated in README
```

---

## Example Complete Ticket

```markdown
# [HAR-012] Add Hybrid Search (Vector + Keyword)

## Descripción

Implement hybrid search combining vector similarity and BM25 keyword matching to improve retrieval relevance for product queries. Currently, pure vector search misses exact product name matches.

## Subagentes Asignados

| Agente | Rol | Archivo |
|--------|-----|---------|
| `@rag-engineer` | Lead: Implementar hybrid search | `.claude/agents/ai/rag-engineer.md` |
| `@python-developer` | Support: Utilidades BM25 | `.claude/agents/backend/python-developer.md` |
| `@performance-tester` | Support: Benchmark latencia | `.claude/agents/qa/performance-tester.md` |
| `@code-reviewer` | Review: Verificar calidad | `.claude/agents/qa/code-reviewer.md` |

## Documentación Requerida

| Documento | Propósito |
|-----------|-----------|
| [PROJECT-SPEC.md](../PROJECT-SPEC.md) | RAG configuration specs |
| [rag-engineer.md](../.claude/agents/ai/rag-engineer.md) | RAG implementation patterns |
| [revel-beauty-knowledge-base.md](../../data/products/revel-beauty-knowledge-base.md) | Product data structure |

## Archivos Afectados

| Archivo | Acción | Descripción |
|---------|--------|-------------|
| `src/rag/retrieval.py` | Modify | Add hybrid_search method |
| `src/rag/keyword_search.py` | Create | BM25 search implementation |
| `src/config.py` | Modify | Add hybrid search config |
| `tests/test_rag_hybrid.py` | Create | Hybrid search tests |

## Contexto Técnico

Actualmente el RAG usa solo búsqueda vectorial:
- Funciona bien para queries semánticos ("help with aging")
- Falla con nombres exactos ("Youth Lift Face Cream")

Hybrid search combina:
- **Vector search:** Captura intención semántica
- **Keyword search:** Captura coincidencias exactas

## Solución Propuesta

### 1. Implementar BM25 keyword search

```python
# src/rag/keyword_search.py
from rank_bm25 import BM25Okapi
from typing import list

class KeywordSearch:
    def __init__(self, documents: list[dict]):
        self.documents = documents
        tokenized = [doc["text"].lower().split() for doc in documents]
        self.bm25 = BM25Okapi(tokenized)

    def search(self, query: str, top_k: int = 10) -> list[dict]:
        tokens = query.lower().split()
        scores = self.bm25.get_scores(tokens)
        top_indices = scores.argsort()[-top_k:][::-1]
        return [
            {"doc": self.documents[i], "score": scores[i]}
            for i in top_indices if scores[i] > 0
        ]
```

### 2. Agregar hybrid search al RAGService

```python
# src/rag/retrieval.py
async def hybrid_search(
    self,
    query: str,
    top_k: int = 5,
    vector_weight: float = None,
    keyword_weight: float = None
) -> str:
    vector_weight = vector_weight or settings.hybrid_vector_weight
    keyword_weight = keyword_weight or settings.hybrid_keyword_weight

    # Vector search
    embedding = await self.embedder.embed(query)
    vector_results = await self.vector_store.query(embedding, top_k=top_k*2)

    # Keyword search
    keyword_results = self.keyword_search.search(query, top_k=top_k*2)

    # Combine with RRF (Reciprocal Rank Fusion)
    combined = self._reciprocal_rank_fusion(
        vector_results, keyword_results,
        vector_weight, keyword_weight
    )

    return self._format_context(combined[:top_k])
```

### 3. Configuración

```python
# src/config.py
class Settings(BaseSettings):
    # Existing...

    # Hybrid search
    hybrid_search_enabled: bool = True
    hybrid_vector_weight: float = 0.7
    hybrid_keyword_weight: float = 0.3
```

## Antes y Después

### Antes
```python
# Solo vector search
async def retrieve(self, query: str) -> str:
    embedding = await self.embedder.embed(query)
    results = await self.vector_store.query(embedding, top_k=5)
    return self._format_context(results)
```

### Después
```python
# Hybrid search (vector + keyword)
async def retrieve(self, query: str) -> str:
    if settings.hybrid_search_enabled:
        return await self.hybrid_search(query)
    else:
        # Fallback to vector only
        embedding = await self.embedder.embed(query)
        results = await self.vector_store.query(embedding, top_k=5)
        return self._format_context(results)
```

## Criterios de Aceptación

- [ ] `KeywordSearch` clase implementada con BM25
- [ ] `hybrid_search` método agregado a `RAGService`
- [ ] Configuración via env vars (`HYBRID_VECTOR_WEIGHT`, etc.)
- [ ] Reciprocal Rank Fusion implementado correctamente
- [ ] Test: query "Eye Cream" retorna Eye Cream como top result
- [ ] Test: query "help with wrinkles" retorna productos relevantes
- [ ] Latencia: incremento < 100ms vs vector-only
- [ ] Coverage > 85% en nuevos archivos
- [ ] Documentación actualizada en PROJECT-SPEC.md

## Dependencias

- **Depende de:** #11 (RAG retrieval service)
- **Bloquea:** Ninguno

## Metadata

- **Priority:** P1
- **Epic:** 1.2 - RAG Pipeline
- **Phase:** 1 - MVP
- **Labels:** `epic-rag`, `ai`, `P1-high`, `phase-1-mvp`
```

---

## Checklist Before Creating Ticket

- [ ] Descripción clara del problema y solución
- [ ] Subagentes asignados con roles específicos
- [ ] Documentación relevante listada
- [ ] Archivos afectados identificados
- [ ] Código de ejemplo incluido
- [ ] Criterios de aceptación verificables
- [ ] Dependencias identificadas
- [ ] Metadata completa

---

*Version: 1.0.0*
*Created: January 2025*
