# Skill: Auditoría de proyecto e implementación

## Objetivo

Determinar si una implementación propuesta o realizada responde a la solicitud y al plan aprobados, y comunicar con evidencia los riesgos, desviaciones y verificaciones. La auditoría se realiza únicamente después de que el usuario haya aprobado explícitamente el plan; puede cubrir la preparación previa, el seguimiento durante y la revisión posterior a la implementación. Auditar no sustituye la aprobación del usuario ni autoriza cambios por sí misma.

## Activación

Usa esta skill para auditar el trabajo asociado a un plan de implementación aprobado: antes de implementar, durante la implementación o después de completarla. La elaboración, presentación y aprobación del plan se rigen por `.agents/behaviour.md` y quedan fuera de esta skill.

## Inputs

### Información de la solicitud

- Solicitud del usuario y resultado esperado.
- Plan de implementación aprobado explícitamente por el usuario, incluidos su alcance y las decisiones que contiene.
- Criterios de aceptación proporcionados, si existen.
- Archivos, componentes o áreas afectadas que se conozcan.

### Información de ejecución

Para una auditoría durante o después de implementar, utiliza también, si están disponibles:

- Cambios realizados o diff.
- Resultado de pruebas y comprobaciones.
- Decisiones o aprobaciones adicionales recibidas durante el trabajo.

### Fuentes de contexto que debe consultar el agente

Antes de comenzar cualquier auditoría, revisa las fuentes pertinentes en este orden:

1. `AGENTS.md` y las instrucciones aplicables a los archivos implicados.
2. Los archivos de `memory-bank/` pertinentes; como referencia base, `projectbrief.md`, `techContext.md` y `progress.md` si existen.
3. Los archivos `CONTEXT` pertinentes (`CONTEXT.md`, `CONTEXT.es.md` u otras variantes existentes).
4. Los `README` pertinentes: primero los de la raíz y después los de las carpetas afectadas.
5. El código, configuración, documentación y pruebas directamente relacionados con la solicitud.

Estos documentos son fuentes de contexto, no autorización para cambiar archivos. Distingue hechos observados, propuestas y decisiones aprobadas.

### Inputs faltantes

- Inicia la auditoría únicamente después de que el usuario haya aprobado explícitamente el plan. La preparación y aprobación del plan corresponden al proceso definido en `.agents/behaviour.md`, no a esta skill.
- Si falta información necesaria para determinar alcance, comportamiento o aceptación, enumera lo que falta y pregunta al usuario. No inventes requisitos ni decidas por cuenta propia.
- Si un input opcional no está disponible, declara cómo limita la auditoría y continúa solo cuando sea posible hacerlo sin suposiciones críticas.

## Outputs

### Después de aprobar el plan y antes de implementar: informe de auditoría previa

El propósito de este informe es que el usuario pueda decidir si da el visto bueno para avanzar, solicita más análisis del estado actual o pausa el trabajo. Preséntalo de forma concisa y adaptada al tamaño de la solicitud; comienza con un **resumen ejecutivo** de los hallazgos más importantes y críticos, los riesgos principales, las incertidumbres o decisiones pendientes y una recomendación razonada. Expón las opciones de decisión relevantes sin decidir en nombre del usuario. La aprobación previa del plan no equivale al visto bueno para continuar tras esta auditoría.

1. **Resultado de auditoría:** el plan aprobado está suficientemente definido para iniciar / se requiere aclaración / se requiere una decisión por riesgo, discrepancia o cambio de dirección. No lo llames aprobación de implementación.
2. **Problema y objetivo:** qué se intenta resolver y qué evidencia del repositorio lo respalda; identifica supuestos e información no verificada.
3. **Alcance:** inclusiones, exclusiones, dependencias, áreas afectadas y trabajo que excedería la solicitud.
4. **Cambios previstos:** archivos o áreas que se modificarían, qué cambiaría y cómo se espera que funcione.
5. **Riesgos y efectos posibles:** causa, impacto potencial, incertidumbre y mitigación o decisión requerida.
6. **Dirección del proyecto:** si el plan parece mantenerla o cambiarla, con las fuentes pertinentes.
7. **Verificación prevista:** pruebas o comprobaciones relevantes y límites de lo que pueden demostrar.
8. **Preguntas pendientes:** aclaraciones o decisiones adicionales necesarias antes de implementar; distingue estas cuestiones de la aprobación ya otorgada al plan.
9. **Decisión solicitada al usuario:** elegir si da el visto bueno para avanzar dentro del plan aprobado, solicita análisis adicional del estado actual o pausa hasta resolver los puntos indicados. Si hay un riesgo crítico o una decisión pendiente, recomienda pausar el trabajo afectado.

### Durante la implementación: avisos de seguimiento

Comunica sin demora y resume lo necesario para que el usuario decida si continuar, pedir análisis adicional o pausar:

- Diferencias entre el estado encontrado y el plan aprobado.
- Riesgos nuevos, posibles errores, regresiones o efectos secundarios.
- Trabajo que parezca exceder el alcance y decisiones que se necesiten.
- Si es necesario detenerse, la causa, las opciones relevantes y la aprobación o información que falta.

### Después de implementar: informe de auditoría final

Comienza con un resumen ejecutivo de los resultados, las desviaciones y los riesgos residuales más importantes. Después, informa:

1. Cambios previstos frente a cambios realizados y cualquier desviación, indicando si fue aprobada.
2. Archivos modificados y rangos de líneas afectados; identifica expresamente archivos o elementos sin líneas cuando corresponda.
3. Cómo responde cada cambio a la solicitud y al plan aprobado.
4. Pruebas y comprobaciones ejecutadas, con sus resultados; si no se ejecutaron, indícalo y explica brevemente por qué.
5. Riesgos residuales, limitaciones y asuntos aún no verificados.
6. **Siguiente decisión:** recomienda, según la evidencia, avanzar con el siguiente paso dentro del alcance aprobado, analizar más el estado actual o pausar; deja la decisión al usuario.

## Criterios de aceptación

La auditoría se inicia con un plan aprobado y se considera completa únicamente si el informe de la fase correspondiente cumple todos los criterios aplicables:

- [ ] Confirma que existe un plan aprobado explícitamente y que identifica la solicitud y el resultado esperado; si no puede confirmar la aprobación, detiene la auditoría y solicita aclaración.
- [ ] Resume la evidencia pertinente del repositorio y diferencia hechos observados, propuestas, estimaciones y decisiones aprobadas.
- [ ] Delimita qué está dentro y fuera del alcance, identifica dependencias y señala trabajo potencialmente adicional.
- [ ] Enumera cambios previstos con ubicación y comportamiento esperado antes de implementar; después, compara lo previsto con lo realizado.
- [ ] Hace visibles los riesgos materiales con causa e impacto potencial, señala incertidumbre y especifica mitigación o decisión necesaria cuando aplique.
- [ ] Indica si detecta un posible cambio de dirección del proyecto, cita las fuentes que sustentan la comparación y no avanza en esa parte sin decisión y aprobación explícitas.
- [ ] Registra las verificaciones realmente ejecutadas y sus resultados, o declara que no se ejecutaron y explica brevemente por qué.
- [ ] Identifica dudas, inputs faltantes y limitaciones que impiden concluir, y solicita aclaraciones cuando sean necesarias.
- [ ] Presenta un resumen ejecutivo de los hallazgos críticos, riesgos, incertidumbres y decisiones pendientes; incluye una recomendación razonada y opciones para que el usuario decida si avanzar, pedir más análisis o pausar.
- [ ] No presenta la auditoría como aprobación del plan, del alcance adicional ni de la implementación; la aprobación corresponde al usuario.

## Procedimiento de auditoría

### 1. Después de aprobar el plan y antes de implementar

Una vez que el usuario haya aprobado explícitamente el plan:

1. Inspecciona el proyecto y los archivos relevantes para entender el estado actual, las convenciones, las dependencias y los límites documentados. No infieras que una guía o propuesta equivale a una decisión adoptada.
2. **Audita el problema:** valida qué problema se intenta resolver y qué evidencia del repositorio lo respalda. Señala supuestos, ambigüedades o información que falta.
3. **Audita la solicitud:** comprueba que el plan responde a la petición explícita del usuario y separa claramente lo solicitado de las inferencias o propuestas.
4. **Audita el alcance:** identifica inclusiones, exclusiones, dependencias, archivos o áreas afectadas y cualquier trabajo que exceda la petición.
5. Evalúa coherencia con el estado y la dirección documentados, viabilidad aparente, riesgos, efectos secundarios y verificabilidad. No presentes una revisión limitada del repositorio como auditoría legal, de seguridad u otra evaluación especializada completa.
6. Entrega el informe de auditoría previa definido en «Outputs» antes de implementar. Resume los hallazgos críticos y recomienda avanzar, solicitar más análisis o pausar, explicando la evidencia y las consecuencias relevantes. La aprobación previa del plan no sustituye el visto bueno del usuario tras leer la auditoría; no continúes con la implementación hasta recibir su decisión explícita.
7. Si la auditoría descubre una decisión nueva, un cambio de alcance o falta de detalle, no lo incorpores silenciosamente. Solicita dirección y aprobación explícitas antes de actuar.

### 2. Durante la implementación

- Contrasta el trabajo real con el plan y el alcance aprobados.
- Si los archivos, dependencias, arquitectura o comportamientos encontrados contradicen el plan, detente en el punto que requiera una decisión; explica la discrepancia, sus opciones y sus consecuencias, y espera instrucciones.
- Señala en cuanto se detecten riesgos nuevos, efectos secundarios, errores potenciales o cambios fuera del alcance. No ocultes ni minimices riesgos relevantes.
- No amplíes el alcance sin aprobación explícita. Comunica cualquier diferencia material respecto al plan.

### 3. Después de implementar

- Inspecciona los cambios realizados y compáralos con la solicitud y el plan aprobados.
- Ejecuta las pruebas o comprobaciones pertinentes disponibles para el área afectada. No afirmes que se realizó una validación que no se ejecutó; si no hay pruebas apropiadas o no se ejecutaron, indícalo y explica brevemente por qué.
- Entrega el informe de auditoría final definido en «Outputs».
- Mantén diferenciados los hechos comprobados, los riesgos estimados y los asuntos sin verificar.

## Señalización de riesgos y cambios de dirección

- Si el plan presenta riesgos importantes, destácalos de forma visible al inicio del informe, por ejemplo:

  > **⚠️ RIESGOS IMPORTANTES** — [riesgo, causa, impacto posible, incertidumbre y mitigación o decisión necesaria].

- Prioriza los riesgos y describe la causa, el impacto potencial y la información disponible; no presentes estimaciones como hechos confirmados.
- Si el plan parece cambiar la dirección del proyecto, indícalo explícitamente antes de implementar. Explica qué dirección o decisión documentada podría cambiar, por qué y qué aprobación se necesita. Cita las rutas pertinentes revisadas.
- Si hay riesgos altos o un cambio de dirección no aprobado, no avances con la parte afectada hasta recibir una decisión y aprobación explícitas del usuario.

## Planes demasiado genéricos

Si el plan aprobado no permite determinar cambios, comportamiento o verificaciones concretas:

1. Indica que no tiene suficiente detalle para una auditoría fiable o una implementación controlada.
2. Enumera los temas o áreas que abarca y las decisiones que faltan en cada una.
3. Explica qué ambigüedades impiden estimar el alcance, los riesgos o los criterios de aceptación.
4. Recomienda dividir la petición en cambios más pequeños y verificables; presenta cualquier descomposición como propuesta, no como alcance aprobado.
5. Solicita al usuario que concrete las partes o decisiones pendientes; no avances en el trabajo afectado hasta recibir instrucciones y aprobación explícitas de cualquier ajuste al plan.
