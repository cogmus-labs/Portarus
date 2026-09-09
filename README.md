# Índice de `docs/`

> Reorganizado 2026-08-17: la raíz tenía 32 archivos sueltos. Ahora tiene 3 + este índice,
> y todo lo demás está clasificado por carpeta.
>
> **Si estás arrancando una sesión, no empieces aquí** — empieza por
> [`../GETONTRACK.md`](../GETONTRACK.md).

## Los tres vivos (raíz)

| Archivo | Qué es |
|---|---|
| [`portarus_info.md`](portarus_info.md) | ⭐ **El documento maestro.** Qué es Portarus, marca, capacidades, scope de lanzamiento, arquitectura, pipeline de deploy, convenciones. Punto de entrada de todo. |
| [`PENDING.md`](PENDING.md) | **La lista de trabajo viva.** Launch blockers y prioridades. El trabajo por defecto del proyecto es avanzar esta lista. |
| [`main_business.md`](main_business.md) | Documento maestro de negocio: posicionamiento, el problema, las 6 capacidades en detalle, envelope de entrega, precios, ICP. |

## Carpetas

### [`cro/`](cro/) — conversión y landing
El grupo más grande. Dividido en dos, porque son cosas distintas:

- **[`cro/home/`](cro/home/)** — trabajo concreto sobre el home de Portarus. Contiene una
  cadena histórica que conviene leer en orden: `HOME_STRATEGY.md` (plan) →
  `HOME_CONVERSION_LADDER_SPEC.md` (spec detallado) → `HOME_CRO_AUDIT.md` (auditoría del
  spec contra evidencia) → `HOME_CRO_REMEDIATION.md` (arreglos con criticidad P0/P1/P2).
  Más `ACTIVATION_SPEC.md` (onboarding y time-to-value, el hermano del spec del home),
  `LANDING_AUDIT_HOMEPROP.md`, `LANDING_STORYTELLING_REVIEW.md`,
  `solution-visuals-proposal.md` y `new_html_estilos.md`.
- **[`cro/research/`](cro/research/)** — investigación reutilizable, **no** específica de
  Portarus. Esto se consulta, no se archiva: `section-audit-checklist.md` (checklist de 62
  criterios para auditar cualquier sección de landing), `landing-page-strategies.md`
  (estudios de conversión) y `headline-research-clarity-vs-persuasion.md`.

### [`business/`](business/) — negocio y marca
`main_business.md` vive en la raíz por ser fuente de verdad; aquí está el resto:
`MERCADEO_FINAL.md` (informe CMO de crecimiento), `PRODUCT_NAMING.md` (la investigación de
naming, **ya cerrada** — el nombre es Portarus), y los docs de contexto y GTM de Cogmus.

### [`paper/`](paper/) — el paper del DPN
`PAPER_DPN_ESTRATEGIA.md` (estrategia de publicación), `PAPER_DPN_REVIEW_INTRO_v1.md`
(review hostil estilo NeurIPS de la intro) y el borrador
`Now_Perception_Is_All_You_Need.pdf`.

### [`architecture/`](architecture/) — arquitectura técnica
Arquitectura del worker, flujo de request, payloads y notificaciones de respuesta, refactors
del envelope y del dashboard.

### [`worker/`](worker/) — QA del worker
`QA_GAP_ANALYSIS.md` (fuente de verdad de los GAPs), `QA_TEST_MATRIX.md`,
`QA_RELEASE_PROCESS.md`, `AUDIT_STATUS.md`. El handoff para retomar el QA está en
[`../WORKER_QA_HANDOFF.md`](../WORKER_QA_HANDOFF.md).

### [`core/`](core/) — referencia técnica
`ENV_AND_SECRETS.md` (estructura de todos los `.env` + Account ID de Cloudflare),
`TECH_STACK.md`, `DESIGN_GUIDELINES.md`, `CODING_knowledge.md`, `MIGRATION_GUIDE.md`.

### [`audits/`](audits/) — auditorías
`auditoria-seguridad.md` (seguridad, ronda 6, mayo 2026 — sin vulnerabilidades activas),
más las auditorías de production-readiness y del worker de abril.

### [`ideas/`](ideas/) — sin cocinar
Notas y borradores sin pulir. No son decisiones.

### [`dpn/`](dpn/) — documentación del DPN

### [`archive/`](archive/) — 🗄️ histórico, no accionable
`CHANGELOG.md` (congelado — **no se actualiza nunca**), el plan y el handoff de la
remediación de auditoría **abandonada** (se hará una nueva), y productos retirados.
No retomes trabajo desde aquí.

### `.olds/` — restos anteriores, sin clasificar
