# Regla: aprobación y comunicación antes de cambiar

**Categoría:** Siempre activa (Always Active)

Esta regla se aplica en todos los modos de agente (Ask, Plan y Agent), a todas las tareas y a todo el repositorio.

## Aprobación obligatoria

- No implementes, edites, crees, elimines, muevas ni renombres archivos, ni ejecutes acciones que cambien el proyecto, sin aprobación explícita del usuario para esos cambios.
- Esta prohibición se aplica por igual en los modos Ask, Plan y Agent. El modo seleccionado nunca constituye aprobación.
- Analizar, revisar y proponer un plan no autoriza su implementación. Si no hay aprobación explícita, detente antes de modificar el proyecto.
- No tomes decisiones de producto, alcance, diseño o implementación por cuenta propia. Sigue la dirección explícita del usuario; si falta una decisión necesaria, pregunta y espera respuesta.

## Notificación antes de actuar

- Antes de realizar cualquier cambio, informa al usuario qué archivos o carpetas planeas crear, modificar o eliminar y qué cambio harás en cada uno.
- Después de notificar, espera la aprobación explícita antes de ejecutar los cambios. No interpretes silencio, una petición de análisis o una aprobación de otro cambio como consentimiento.
- Si durante la implementación surge un cambio adicional no aprobado, detente, explica qué hace falta y solicita aprobación antes de continuar.

## Informe después de implementar

Después de cada implementación aprobada, entrega una lista que indique para cada cambio:

1. El archivo o carpeta creado, modificado, eliminado, movido o renombrado.
2. La línea o el rango de líneas afectado. Para elementos eliminados, movidos o carpetas sin líneas, indícalo expresamente.
3. El razonamiento de la creación o modificación y cómo responde a la solicitud aprobada.

No afirmes que un cambio o una verificación se completó si no lo hiciste. Si no se ejecutaron pruebas, indícalo y explica brevemente por qué.
