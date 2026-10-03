# Plantilla Agencia Evolutiva

Una AGENCIA de empleados virtuales IA que funciona sobre opencode. El usuario habla solo con el **director**, que orquesta el trabajo del resto de la agencia (empleados, revisor, reclutador) y la mantiene en mejora continua.

## Uso rápido
1. Abre opencode en esta carpeta.
2. Habla con el agente **director** (es el agente por defecto). Encárgale responsabilidades, funciones, objetivos, contexto, entregables y criterios de "completado". La agencia se adapta sola y crea los recursos que necesite.
3. Comandos disponibles:
   - `/encargo <trabajo>` — encarga un trabajo completo (intake → ejecución → revisión → entrega → mejora).
   - `/constitucion` — (re)constituye la agencia: carta constitucional y recursos iniciales.
   - `/dotacion` — inventario de la agencia (empleados, skills, trabajos activos, estado).

## Primer despliegue (repo clonado)
1. Clona este repo y abre opencode en la carpeta clonada.
2. Ejecuta `/constitucion`: el director te entrevistará (contexto, responsabilidades, funciones, objetivos, entregables, límites, directrices fundamentales, normas operativas y procedimientos) y creará todos los recursos iniciales de forma completa.

## Cómo funciona
- Los agentes son empleados con expediente (`plantilla/empleados/`) y competencias (skills en `.opencode/skills/`, cargadas bajo demanda).
- Cada trabajo queda en `memoria/trabajos/<id>/` con encargo, contrato RACI y plan; los entregables van a `salida/<id>/`.
- La agencia se auto-mejora: consolida lecciones y conocimiento de dominio (`memoria/conocimiento/`), actualiza expedientes, skills, procedimientos (SoP) y normas operativas, promueve scripts a tools de plugin (`.opencode/plugin/`) y commitea sus cambios automáticamente.
- Límites: la agencia respeta siempre `constitucion/limites.md`; si un trabajo excede un límite, te consulta antes de seguir.

## Estructura
- `backlog/` — ideas y funcionalidades (`backlog.md`: In Progress, Pending, In Review). Completadas/discartadas → `archived/backlog-archived-AAAA-MM-DD.md` (`Completed` con `- [x]`, `Discarted` con `- [ ]`).
- `constitucion/` — carta evolutiva: contexto, responsabilidades, funciones, objetivos, entregables, límites, directrices (fundamentales, solo usuario), normas operativas (funcionales/técnicas) y procedimientos SoP.
- `plantilla/empleados/` — expedientes de empleados.
- `memoria/` — trabajos, feedback, conocimiento de dominio, lecciones y estado del ciclo de vida.
- `salida/` — entregables por trabajo.
- `.opencode/` — agentes, skills, tools (plugin) y comandos de la agencia.

## Notas
- Tras crear o modificar agentes, skills, comandos o plugins, reinicia opencode para que se activen. El director puede estrenarlos antes con `opencode run` (sesión hija) y te avisará del restart pendiente.
- Los cambios de conocimiento se commitean automáticamente; los de alto riesgo (config, permisos, modelos, MCP) requieren tu aprobación.
