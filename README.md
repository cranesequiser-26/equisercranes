# Claude Code Skills — Colección Equiser Cranes

Colección curada de **skills para Claude Code** integrados desde la lista de repositorios
proporcionada. Los skills enfocados están **activos** en `.claude/skills/` (se cargan
automáticamente); los catálogos masivos (ciberseguridad, negocio, NVIDIA, científicos)
viven en `skills-library/` para activarse bajo demanda y no saturar el contexto.

## Cómo funciona

- **`.claude/skills/`** — 220 skills activos. Claude Code los descubre automáticamente
  al trabajar en este repo (o cópialos a `~/.claude/skills/` para tenerlos globalmente).
  Ver el listado completo en [`CATALOG.md`](./CATALOG.md).
- **`skills-library/`** — 1.634 skills adicionales (817 ciberseguridad + 346 negocio +
  321 NVIDIA + 150 científicos) **no** auto-activos. Para activar uno:
  ```bash
  cp -R skills-library/<coleccion>/<nombre> .claude/skills/
  ```
  Ver [`skills-library/README.md`](./skills-library/README.md).

> Se separó así a propósito: cargar ~1.850 descripciones de skills en cada sesión
> ralentizaría mucho a Claude Code. El núcleo activo es usable; la biblioteca es un
> almacén organizado listo para usar.

## Skills activos por fuente

| Fuente | Skills | Tema |
|---|---|---|
| [obra/superpowers](https://github.com/obra/superpowers) | 14 | Flujos de desarrollo: TDD, debugging sistemático, planes, code review, git worktrees |
| [anthropics/skills](https://github.com/anthropics/skills) | 17 | Oficiales de Anthropic: docx/pdf/pptx/xlsx, mcp-builder, skill-creator, canvas, frontend-design, brand |
| [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) | 24 | Ingeniería: TDD, spec/source-driven, debugging, seguridad, performance, CI/CD, code review |
| [Joannis/claude-skills](https://github.com/Joannis/claude-skills) | 16 | Swift/SwiftNIO, concurrencia, Postgres, Hummingbird, diseño de librerías |
| [JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | 7 | Commits, review, compresión y stats de contexto estilo "caveman" |
| [DietrichGebert/ponytail](https://github.com/DietrichGebert/ponytail) | 6 | Auditoría, deuda técnica, review y "gain" de contexto (código minimalista) |
| [kepano/obsidian-skills](https://github.com/kepano/obsidian-skills) | 5 | Obsidian: CLI, bases, JSON Canvas, markdown, defuddle |
| [angular/skills](https://github.com/angular/skills) | 2 | Oficiales de Angular: developer, new-app |
| [coderabbitai/skills](https://github.com/coderabbitai/skills) | 2 | Code review y autofix (CodeRabbit) |
| [blader/humanizer](https://github.com/blader/humanizer) | 1 | Humanizar texto generado por IA |
| [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) | 48 | Marketing: SEO, emails, social, PR, copy, analytics, prospecting |
| [mattpocock/skills](https://github.com/mattpocock/skills) | ~37 | Ingeniería y productividad TypeScript (grill-me, tdd, code-review, research…) |
| [zubair-trabzada/geo-seo-claude](https://github.com/zubair-trabzada/geo-seo-claude) | 15 | GEO / SEO para motores de IA (auditoría, schema, llms.txt, citabilidad) |
| [leonxlnx/taste-skill](https://github.com/leonxlnx/taste-skill) | 13 | Diseño / "buen gusto": brandkit, redesign, imagegen, brutalist/minimalist |
| [nextlevelbuilder/ui-ux-pro-max-skill](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) | 7 | UI/UX: design system, branding, banners, slides, ui-styling |
| [alexgreensh/token-optimizer](https://github.com/alexgreensh/token-optimizer) | 4 | Optimización de tokens, coaching, dashboard, fleet auditor |
| [blader/napkin](https://github.com/blader/napkin) | 1 | Napkin math / estimaciones rápidas |
| [pbakaus/impeccable](https://github.com/pbakaus/impeccable) | 1 | Calidad de código impecable |

## Skills en biblioteca (`skills-library/`)

| Fuente | Skills | Tema |
|---|---|---|
| [mukul975/Anthropic-Cybersecurity-Skills](https://github.com/mukul975/Anthropic-Cybersecurity-Skills) | 817 | SOC, DFIR, threat hunting, detección, hardening, compliance |
| [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) | 346 | Negocio, finanzas, C-level, product, engineering, compliance, research |
| [NVIDIA/skills](https://github.com/NVIDIA/skills) | 321 | GPU/CUDA, TAO Toolkit, DOCA, Dynamo, Triton, inferencia y frameworks NVIDIA |
| [K-Dense-AI/claude-scientific-skills](https://github.com/K-Dense-AI/claude-scientific-skills) | 150 | Ciencia: bioinformática, forecasting, química, formatos de datos (BIDS…) |

## Herramientas y frameworks (referencias externas)

Estos repositorios de la lista **no son skills de Claude Code** — son aplicaciones,
librerías o frameworks independientes. No se pueden "incluir como skill"; se instalan y
ejecutan por su cuenta. Se documentan aquí como referencia:

| Proyecto | Qué es |
|---|---|
| [anthropics/claude-code](https://github.com/anthropics/claude-code) | El propio CLI de Claude Code |
| [MoonshotAI/kimi-code](https://github.com/MoonshotAI/kimi-code) | Agente de código (Kimi) |
| [microsoft/markitdown](https://github.com/microsoft/markitdown) | Convierte documentos (PDF/Office/…) a Markdown |
| [microsoft/playwright](https://github.com/microsoft/playwright) | Automatización de navegador / testing E2E |
| [yamadashy/repomix](https://github.com/yamadashy/repomix) | Empaqueta un repo en un solo archivo para LLMs |
| [open-webui/open-webui](https://github.com/open-webui/open-webui) | UI web para LLMs locales/remotos |
| [1Panel-dev/maxkb](https://github.com/1Panel-dev/maxkb) | Base de conocimiento + chatbot RAG |
| [vllm-project/semantic-router](https://github.com/vllm-project/semantic-router) | Enrutado semántico de peticiones LLM |
| [Shubhamsaboo/awesome-llm-apps](https://github.com/Shubhamsaboo/awesome-llm-apps) | Colección de apps LLM de ejemplo |
| [supermemoryai/supermemory](https://github.com/supermemoryai/supermemory) | Capa de memoria para IA |
| [thedotmack/claude-mem](https://github.com/thedotmack/claude-mem) | Memoria persistente para Claude |
| [alibaba/page-agent](https://github.com/alibaba/page-agent) | Agente que opera páginas web |
| [ValueCell-ai/valuecell](https://github.com/ValueCell-ai/valuecell) | Framework de agentes |
| [VRSEN/OpenSwarm](https://github.com/VRSEN/OpenSwarm) | Orquestación multi-agente |
| [Panniantong/agent-reach](https://github.com/Panniantong/agent-reach) | Alcance/outreach con agentes |
| [Hainrixz/whatsapp-agentkit](https://github.com/Hainrixz/whatsapp-agentkit) | Kit de agentes para WhatsApp |
| [jamiepine/voicebox](https://github.com/jamiepine/voicebox) | Herramienta de voz |
| [steipete/CodexBar](https://github.com/steipete/CodexBar) | App de barra de menú para Codex |
| [garrytan/gstack](https://github.com/garrytan/gstack) | Stack/plantilla de proyecto |
| [cporter202/API-mega-list](https://github.com/cporter202/API-mega-list) | Catálogo enorme de APIs por categoría (referencia, no skills) |
| [Jpisnice/shadcn-ui-mcp-server](https://github.com/Jpisnice/shadcn-ui-mcp-server) | Servidor MCP para componentes shadcn/ui |
| [browsermcp/mcp](https://github.com/browsermcp/mcp) | Servidor MCP para controlar el navegador |
| [21st-dev/magic-mcp](https://github.com/21st-dev/magic-mcp) | Servidor MCP para generar componentes UI |
| [vercel-labs/agent-browser](https://github.com/vercel-labs/agent-browser) | Navegador para agentes (Vercel Labs) |
| [gosom/google-maps-scraper](https://github.com/gosom/google-maps-scraper) | Scraper de Google Maps (Go) |
| [msitarzewski/agency-agents](https://github.com/msitarzewski/agency-agents) | Colección de sub-agentes por área (no son skills SKILL.md) |
| [harness/harness](https://github.com/harness/harness) | Plataforma CI/CD |
| [Mesabloo/diagnose](https://github.com/Mesabloo/diagnose) | Librería de diagnósticos (Haskell) |
| [nv-tlabs/Fixer](https://github.com/nv-tlabs/Fixer) | Herramienta de NVIDIA Toronto AI Lab |
| [JasonHonKL/spy-search](https://github.com/JasonHonKL/spy-search) | Framework de búsqueda/investigación |
| [brokermr810/quantdinger](https://github.com/brokermr810/quantdinger) | Trading cuantitativo |
| [decolua/9router](https://github.com/decolua/9router) · [diegosouzapw/OmniRoute](https://github.com/diegosouzapw/OmniRoute) | Routers de LLM |
| [freecodexyz/free-code](https://github.com/freecodexyz/free-code) · [tashfeenahmed/freellmapi](https://github.com/tashfeenahmed/freellmapi) · [Rishurajgautam24/free-claude-code](https://github.com/Rishurajgautam24/free-claude-code) | Acceso "gratis" a APIs de LLM. ⚠️ Suelen usar proxies/credenciales no autorizados y **pueden violar los ToS del proveedor**. Documentados solo como referencia; no se bundlea código. |
| [h4ckf0r0day/obscura](https://github.com/h4ckf0r0day/obscura) · [temken/obscura](https://github.com/temken/obscura) | Ofuscación / (temken es librería de física de materia oscura). Referencia. |
| [respond-io](https://github.com/respond-io) | Organización (no un repo concreto) de mensajería/atención al cliente. |
| [VoltAgent/awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills) | Lista curada de agent skills (índice, no skills en sí) |

## Excluido a propósito

| Repositorio | Motivo |
|---|---|
| [elder-plinius/G0DM0D3](https://github.com/elder-plinius/G0DM0D3) | Repo de *jailbreak / "godmode"* para saltarse las salvaguardas de modelos de IA. **No se integra.** |

## Estructura

```
.claude/skills/          # 220 skills activos (auto-cargados)
skills-library/
  cybersecurity/         # 817 skills (activar bajo demanda)
  business/              # 346 skills por categoría
  nvidia/                # 321 skills GPU/CUDA/NVIDIA
  scientific/            # 150 skills científicos
CATALOG.md               # listado completo de skills activos
skills-library/README.md # listado de la biblioteca
```

## Créditos

Cada skill conserva la atribución de su repositorio de origen (ver tablas arriba).
Esta colección solo reorganiza contenido público de terceros para uso con Claude Code.
