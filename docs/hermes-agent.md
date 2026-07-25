# Skills recomendados para un agente Hermes (que reporta sus actividades)

Selección curada de la colección de este repo para un **agente Hermes en entrenamiento
que debe enviar reportes de sus actividades**. Ordenado de más a menos directo para ese
caso de uso.

> ⭐ = encaje directo con "reportar actividades".
> Los skills marcados **[activo]** ya están en `.claude/skills/` (Claude Code los carga solo).
> Los **[biblioteca]** se activan copiando su carpeta — comando incluido.

---

## 1. Reporte de actividades (el núcleo de lo que pides)

| Skill | Dónde | Qué hace |
|---|---|---|
| ⭐ `team-communications` | [biblioteca] `business/project-management` | Escribe comunicaciones internas: **updates 3P (Progreso/Planes/Problemas)**, reportes de incidentes, FAQ, newsletters. El formato ideal para que Hermes reporte estado. |
| ⭐ `internal-comms` | [activo] anthropics/skills | Status reports, updates de liderazgo, reportes de incidentes, updates de proyecto. |
| ⭐ `agent-decision-receipts` | [biblioteca] `business/ra-qm-team` | Emite un **recibo firmado y a prueba de manipulación** por cada acción consecuente del agente (deploy, borrar, pagar, dar acceso, decisión de modelo). Trazabilidad de actividad. |
| ⭐ `tc-tracker` | [biblioteca] `business/engineering` | Registra cambios técnicos y **hand-off de trabajo entre sesiones de IA**. |
| ⭐ `collab-proof` | [biblioteca] `business/engineering` | Retro de sesión: qué hizo el agente vs qué dirigiste tú. |
| `decision-logger` | [biblioteca] `business/c-level-advisor` | Registra decisiones en memoria de dos capas (transcripción cruda → decisión aprobada). |

**Activar el paquete de reporte (biblioteca):**
```bash
cp -R skills-library/business/project-management/team-communications .claude/skills/
cp -R skills-library/business/ra-qm-team/agent-decision-receipts       .claude/skills/
cp -R skills-library/business/engineering/tc-tracker                   .claude/skills/
cp -R skills-library/business/engineering/collab-proof                 .claude/skills/
cp -R skills-library/business/c-level-advisor/decision-logger          .claude/skills/
```

---

## 2. Observabilidad, logging y auditoría (medir la actividad)

| Skill | Dónde | Qué hace |
|---|---|---|
| ⭐ `fleet-auditor` | [activo] alexgreensh/token-optimizer | **Audita el gasto de tokens entre sistemas de agentes — incluye Hermes por nombre** (Claude Code, Codex, OpenClaw, **Hermes**, OpenCode). Detecta quemados en idle y mal enrutado de modelos. |
| `token-dashboard` / `token-coach` | [activo] token-optimizer | Dashboard y coaching de uso de tokens por sesión. |
| `observability-and-instrumentation` | [activo] addyosmani/agent-skills | Instrumenta código: logging, métricas, tracing, alerting. |
| `observability-designer` | [biblioteca] `business/engineering` | Estrategia de observabilidad: métricas+logs+traces, SLI/SLO, golden signals. |
| `llm-cost-optimizer` | [biblioteca] `business/engineering` | Optimización de coste/tokens de las llamadas LLM. |
| `nemo-relay-instrument-calls` | [biblioteca] `nvidia` | Envuelve los call-sites de tools/LLM con scopes de instrumentación (telemetría por llamada). |

```bash
cp -R skills-library/business/engineering/observability-designer .claude/skills/
cp -R skills-library/business/engineering/llm-cost-optimizer      .claude/skills/
cp -R skills-library/nvidia/nemo-relay-instrument-calls           .claude/skills/
```

---

## 3. Memoria y hand-off entre sesiones (continuidad del reporte)

| Skill | Dónde | Qué hace |
|---|---|---|
| `close-session` | [activo] awrshift/claude-memory-kit | Ritual de cierre: audita patrones, refresca `MEMORY.md` y **escribe el hand-off de sesión**. |
| `handoff` / `claude-handoff` | [activo] mattpocock/skills | Compacta la conversación en un documento de hand-off para otro agente. |
| `session-management` | [biblioteca] `bootstrap` | Preservación de contexto, resúmenes por niveles, reanudación. |
| `mnemos` | [biblioteca] `bootstrap` | Memoria por tarea (hechos/decisiones/refs/handoffs tipados) anti-compactación. |
| `nemo-rl-session-memory` | [biblioteca] `nvidia` | Memoria de sesión durable para recuperar contexto tras desconexiones. |
| `memory-status` / `self-improving-agent` | [biblioteca] `business/engineering-team` | Salud de la memoria y auto-mejora desde el uso pasado. |

```bash
cp -R skills-library/bootstrap/session-management                 .claude/skills/
cp -R skills-library/bootstrap/mnemos                             .claude/skills/
cp -R skills-library/nvidia/nemo-rl-session-memory                .claude/skills/
cp -R skills-library/business/engineering-team/memory-status      .claude/skills/
cp -R skills-library/business/engineering-team/self-improving-agent .claude/skills/
```

---

## 4. Orquestación multi-agente (entrenar/coordinar a Hermes)

| Skill | Dónde | Qué hace |
|---|---|---|
| ⭐ `agent-workflow-designer` | [biblioteca] `business/engineering` | Diseña workflows multi-agente con **contratos de hand-off** y elección de patrón (secuencial/paralelo/jerárquico). |
| AgentHub: `init` `spawn` `eval` `merge` `status` | [biblioteca] `business/engineering` | Suite de colaboración: lanza N subagentes, los evalúa y reporta **estado del DAG y progreso de cada agente**. |
| `subagent-driven-development` | [activo] superpowers | Ejecuta planes con tareas independientes vía subagentes. |
| `dispatching-parallel-agents` | [activo] superpowers | Despacha 2+ tareas independientes a agentes en paralelo. |
| `do-and-judge` / `judge` | [biblioteca] `context-engineering` | Sub-agente ejecutor + LLM-como-juez con reintento (verificación de resultados). |
| `polyphony` | [biblioteca] `bootstrap` | Orquestación multi-agente con workspaces aislados en Docker. |
| `senior-prompt-engineer` | [biblioteca] `business/engineering-team` | Optimiza prompts y evalúa salidas con un set de evals (útil para entrenar el agente). |

```bash
cp -R skills-library/business/engineering/agent-workflow-designer .claude/skills/
for s in init spawn eval merge status; do cp -R skills-library/business/engineering/$s .claude/skills/; done
cp -R skills-library/context-engineering/do-and-judge             .claude/skills/
cp -R skills-library/context-engineering/judge                    .claude/skills/
cp -R skills-library/bootstrap/polyphony                          .claude/skills/
cp -R skills-library/business/engineering-team/senior-prompt-engineer .claude/skills/
```

---

## Repos fuente más relevantes

| Repo | Por qué encaja con Hermes |
|---|---|
| [alexgreensh/token-optimizer](https://github.com/alexgreensh/token-optimizer) | ⭐ `fleet-auditor` audita **Hermes** por nombre; dashboards de tokens. |
| [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) | Suite `business`: reporting (team-communications), decision-receipts, AgentHub, observability-designer, agent-workflow-designer. |
| [NeoLabHQ/context-engineering-kit](https://github.com/NeoLabHQ/context-engineering-kit) | Verificación con juez, subagentes, trazado de causa raíz. |
| [alinaqi/claude-bootstrap](https://github.com/alinaqi/claude-bootstrap) | Memoria de sesión, `mnemos`, orquestación `polyphony`. |
| [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) | `observability-and-instrumentation`, `documentation-and-adrs`. |
| [awrshift/claude-memory-kit](https://github.com/awrshift/claude-memory-kit) | Cierre de sesión y hand-off. |
| [anthropics/skills](https://github.com/anthropics/skills) | `internal-comms` (reportes de estado/incidentes). |
| [obra/superpowers](https://github.com/obra/superpowers) | Despacho de agentes en paralelo, subagentes. |

**Referencias externas (frameworks, no skills):** `VRSEN/OpenSwarm` (orquestación
multi-agente), `VoltAgent/voltagent`, `supermemoryai/supermemory` y `thedotmack/claude-mem`
(capas de memoria), útiles si Hermes necesita infraestructura de memoria/coordinación fuera
de Claude Code.

---

## Mínimo imprescindible (si solo activas 5)

Para "un agente que envía reportes de sus actividades", empieza por estos:

```bash
cp -R skills-library/business/project-management/team-communications .claude/skills/  # reporte 3P
cp -R skills-library/business/ra-qm-team/agent-decision-receipts     .claude/skills/  # recibo por acción
cp -R skills-library/business/engineering/tc-tracker                 .claude/skills/  # hand-off entre sesiones
cp -R skills-library/business/engineering/observability-designer     .claude/skills/  # logs/métricas/traces
# fleet-auditor e internal-comms ya están activos
```
