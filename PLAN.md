# Plan de Presentación Web — INFODETS

## Stack Tecnológico

| Tecnología | Propósito |
|------------|-----------|
| **Reveal.js** | Framework de slides con transiciones, navegación por teclado, speaker notes |
| **GSAP** | Animaciones avanzadas por slide (entradas, efectos visuales) |
| **Howler.js** | Efectos de sonido al cambiar de slide |
| **HTML + CSS + JS plano** | Sin build tooling. Todo en un único `index.html` con CDNs |

---

## Estructura de las 18 Diapositivas

### Expositor 1 — Visión Estratégica y Funcional (Slides 1–6)

| # | Título | Contenido |
|---|--------|-----------|
| 1 | **Portada** | INFODETS — Sistema de Gestión de Conocimiento Dinámico. Facultad, materia, equipo, fecha |
| 2 | **Problema** | Ciudadanos sin acceso fácil a documentación oficial. Búsqueda manual ineficiente. Información dispersa en PDFs, resoluciones, webs oficiales |
| 3 | **Solución** | Chat RAG multinivel con IA. Búsqueda en documentos oficiales → URLs → web → escalamiento humano. 4 niveles de degradación |
| 4 | **Funcionalidades Core** | Chat con IA con citas, ingesta de documentos PDF, noticias institucionales, dashboard admin, feedback loop de mejora continua |
| 5 | **Roles y Usuarios** | Ciudadanos (invitado), usuarios internos autenticados, administradores. 11 permisos granulares |
| 6 | **Demo Rápida** | Flujo: usuario pregunta → Qdrant busca → Gemini responde con fuentes → streaming SSE |

### Expositor 2 — Arquitectura Técnica y Cloud (Slides 7–12)

| # | Título | Contenido |
|---|--------|-----------|
| 7 | **Arquitectura General** | Diagrama capas: Frontend (Next.js 16 + Mantine) → Backend (FastAPI) → DBs (PostgreSQL + Qdrant) → AI (Gemini + Groq). AWS EC2 |
| 8 | **Frontend** | Next.js 16 App Router, Mantine UI v9, Zustand + TanStack Query, Framer Motion. 15+ rutas, SSR/CSR |
| 9 | **Backend** | FastAPI Python 3.13, SQLAlchemy + Alembic, 20+ endpoints REST, SSE streaming, JWT con Cognito |
| 10 | **Pipeline RAG** | Query → Embedding Gemini 3072d → Qdrant → HyDE → Query Expansion → Cohere Rerank → Gemini → Fallback Groq. Cache semántico (cosine >0.95, TTL 24h) |
| 11 | **Bases de Datos** | PostgreSQL 17.6 en RDS (18 tablas). Qdrant self-hosted Docker (vectores 3072d). Soberanía de datos |
| 12 | **Infraestructura AWS** | EC2 Ubuntu 24.04, RDS PostgreSQL, Cognito. Docker compose (Next.js, FastAPI, Qdrant, n8n). CI/CD GitHub Actions |

### Expositor 3 — Síntesis, Despliegue y Cierre (Slides 13–18)

| # | Título | Contenido |
|---|--------|-----------|
| 13 | **Metodología Ágil** | 6 sprints (S0–S5), 35 user stories (28 implementadas), burndown. Roles P1/P2/P3 |
| 14 | **Despliegue y CI/CD** | GitHub Actions → push a main → SSH a EC2 → docker-compose pull up. Pipeline automático |
| 15 | **Resultados** | MVP operativo en producción. RAG funcional 4 niveles. Validaciones automáticas. Sistema multi-tenant de permisos |
| 16 | **Decisiones Técnicas** | Qdrant vs Pinecone (soberanía). JWT custom vs Cognito (performance). FastAPI vs n8n para PDFs (control) |
| 17 | **Trabajo Futuro** | CloudFront CDN, monitoreo avanzado, más fuentes de datos, mejora de embeddings, app mobile |
| 18 | **Cierre** | Agradecimientos. Enlaces: GitHub, demo. QR code |

---

## Fases de Implementación

### Fase 1 — Esqueleto base
- `index.html` con Reveal.js desde CDN
- 18 slides con títulos placeholder
- Navegación por teclado (← →), click, swipe táctil
- Indicador de progreso (slide X / 18)
- Modo oscuro profesional
- Transiciones default de Reveal.js

### Fase 2 — Contenido completo
- Volcar el contenido detallado en cada slide
- HTML semántico con estructura clara
- Listas, tablas, quotes para cada tema
- Speaker notes integradas (tecla N)

### Fase 3 — Visuales y diagramas
- Diagrama de arquitectura (SVG inline)
- Diagrama del pipeline RAG
- Iconos representativos de cada tecnología
- Animaciones GSAP de entrada por slide
- Transiciones personalizadas

### Fase 4 — Sonido y efectos
- Efectos de sonido con Howler.js al navegar
- Partículas/fondo dinámico
- Animaciones parallax sutiles
- Efecto de escritura para textos clave

### Fase 5 — Pulido final
- Responsividad para proyector 1080p y pantallas 4K
- Modo oscuro/claro toggle
- Exportación a PDF desde navegador
- QR code a demo en vivo
- Performance y carga optimizada
