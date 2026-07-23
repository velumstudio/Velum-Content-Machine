# CLAUDE.md — Velum Content Machine
> Instrucciones para Claude Code. Lee este archivo primero en toda sesión.
> Activo cuando: el loop manual ha corrido 4+ semanas y existen 3 Blueprint clients validados.
> Hasta entonces: este archivo documenta la arquitectura futura. No ejecutes batch automation.

---

## Lo que es este repo

Un sistema de contenido para Velum (@thevelum.studio) — estudio operador estratégico
para creadoras authority-led. Todo el contenido sirve a un objetivo:
**3 clientes validados del Velum Blueprint.**

El sistema produce contenido para Instagram: carousels, reels faceless, y videos de Vera
(AI spokesperson). Nada más hasta que ese objetivo esté cumplido.

---

## Archivos — orden de lectura obligatorio

Antes de ejecutar cualquier tarea de contenido, lee en este orden:

```
1. skills/velum-product-marketing.md     ← contexto de marca, ICP, oferta, voz
2. velum-content-machine/00-brand-constitution.md  ← voz, vocabulario, banned patterns
3. velum-content-machine/01-content-strategy.md    ← pillars, principios, CTA library
4. velum-content-machine/02-format-specs.md        ← specs de producción por formato
5. skills/velum-hook-catalogue.md        ← patrones de hook + ejemplos validados
```

No ejecutes ningún agente sin haber leído estos cinco archivos primero.
No preguntes por contexto que ya está en estos archivos.

---

## Agentes disponibles

| Agente | Archivo | Cuándo usarlo |
|---|---|---|
| Carousel Brief Generator | `velum-content-machine/agents/carousel-agent.md` | Topic → brief completo slide por slide |
| Reel Script Generator | `velum-content-machine/agents/reel-agent.md` | Topic → script de reel faceless |
| Vera Script Writer | `velum-content-machine/agents/vera-script-agent.md` | Topic → script aprobado para Higgsfield |
| Repurposing Agent | `velum-content-machine/agents/repurposing-agent.md` | Pieza validada → formatos derivados |

**Agente pendiente (escribir cuando el gate esté abierto):**
- `velum-content-machine/agents/batch-schedule-agent.md` — genera el plan mensual completo

---

## Comando principal — estrategia mensual

**Disponible cuando:** 4+ semanas de loop manual completadas + 3 Blueprint clients validados.

```bash
claude "genera la estrategia de contenido de [MES]:
- 3 posts por semana, 4 semanas = 12 piezas
- pillar rotation: 2 Authority, 2 Education, 1 Offer, 1 Process por cada 2 semanas
- máximo 2 videos de Vera por mes
- máximo 6 carousels por mes
- hooks asignados desde el catálogo validado
- briefs completos listos para Canva / Higgsfield
- output en formato Notion-ready"
```

**Secuencia de ejecución que Claude Code debe seguir:**

```
PASO 1 — Leer contexto
  → Lee los 5 archivos en orden obligatorio (ver arriba)

PASO 2 — Planificar el batch
  → Distribuye 12 piezas en 4 semanas
  → Aplica pillar rotation correcta
  → Asigna formato a cada pieza
  → Asigna hook del catálogo a cada pieza (prioriza hooks validados)

PASO 3 — Ejecutar agentes en secuencia
  → Para cada pieza del batch:
     - Si carousel → carousel-agent.md
     - Si reel faceless → reel-agent.md
     - Si Vera video → vera-script-agent.md
  → Scripts de Vera: marcar como PENDIENTE DE APROBACIÓN MANUAL
    antes de cualquier generación en Higgsfield

PASO 4 — Output
  → Devuelve el plan completo en este formato por pieza:
     SEMANA [N] · SLOT [A/B/C] · [FECHA SUGERIDA]
     Pillar: [x] · Formato: [x] · Hook pattern: [x]
     [Output del agente correspondiente]
     Status: PENDIENTE APROBACIÓN

PASO 5 — Gate de aprobación
  → Nada pasa a Canva o Higgsfield sin aprobación explícita de Paulina
  → Scripts de Vera requieren aprobación palabra por palabra
  → El sistema produce briefs, no activos finales
```

---

## Comandos adicionales

```bash
# Generar una sola pieza
claude "carousel agent: [topic] · pillar: [x]"
claude "reel agent: [topic] · pillar: [x]"
claude "vera script: [topic] · pillar: [x] · funnel: [top/mid/bottom]"

# Repurposing (solo con señal de performance)
claude "repurposing agent: [título de la pieza publicada] · señal: [saves/DMs/follows]"

# Revisar una pieza contra los 6 principios
claude "revisa este copy contra los 6 principios de contenido de Velum: [copy]"

# Actualizar el hook catalogue con un hook validado
claude "añade al hook catalogue: hook '[texto]' · patrón [N] · publicado en [formato] · señal: [resultado]"
```

---

## Constraints que nunca se saltan

Estos constraints están en el README y en el pipeline. Claude Code no los ignora
aunque el comando no los mencione explícitamente:

- **Scripts de Vera: aprobación manual obligatoria antes de generar en Higgsfield.**
  Cada intento de generación es costoso e irreversible. No hay excepciones.
- **Repurposing solo con señal de performance.** Nunca por suposición.
- **Máximo 2 semanas de producción adelantada.** No planificar más allá.
- **Un CTA por pieza. Nombrado. Específico.** Nunca stack.
- **Vocabulario prohibido:** ver 00-brand-constitution.md. Si aparece en un output, reescribir antes de devolver.
- **Sin caras, sin lifestyle, sin motivational language.** Faceless siempre.

---

## Gate de activación — no ignorar

Este sistema de batch automation **no se activa hasta que:**

- [ ] El loop manual ha corrido 4+ semanas consecutivas (3 posts/semana)
- [ ] 3 Blueprint clients están validados y pagados
- [ ] `batch-schedule-agent.md` está escrito y revisado
- [ ] Paulina ha dado el go explícito

Si cualquiera de estas condiciones no está cumplida, Claude Code puede ejecutar
agentes individuales bajo demanda — pero no el comando de estrategia mensual completa.

---

## Estructura del repo

```
velum-content-machine/
  README.md                        sistema overview + constraints
  00-brand-constitution.md         brand DNA — load first
  01-content-strategy.md           pillars, cadence, principles
  02-format-specs.md               production specs per format
  03-pipeline.md                   weekly operating loop
  agents/
    carousel-agent.md
    reel-agent.md
    vera-script-agent.md
    repurposing-agent.md
    batch-schedule-agent.md        ← pendiente de escribir

skills/
  velum-product-marketing.md       context file — todos los skills lo leen primero
  velum-social-skill.md
  velum-copy-skill.md
  velum-offer-skill.md
  velum-hook-catalogue.md          living document — actualizar tras cada Emplifi review

CLAUDE.md                          este archivo
```

---
*— Velum — @thevelum.studio — · CLAUDE.md v1.0 · July 2026*
*Activo post-validación. Hasta entonces: documenta, no ejecuta.*
