# Regla: no usar dependencias ni datos externos sin autorización

**Categoría:** Siempre activa (Always Active)

Esta regla se aplica a todo el repositorio y a todas las tareas.

## Dependencias y librerías

- No instales ni importes paquetes o librerías externos salvo que estén declarados como dependencia en el `package.json` aplicable o que el desarrollador haya dado aprobación explícita para usarlos.
- Antes de proponer añadir una dependencia que no esté declarada, solicita confirmación explícita al desarrollador. No ejecutes comandos de instalación ni presentes la instalación como decidida hasta recibir esa confirmación.
- La aprobación para una librería no autoriza otras dependencias. Verifica cada paquete por separado.

## Fuentes de datos externas

- No consultes Internet, APIs, sitios web, repositorios externos ni hagas scraping para obtener información del proyecto sin autorización directa del desarrollador.
- No descargues, leas ni incorpores archivos externos al repositorio sin esa autorización.
- Basa el análisis y los cambios únicamente en los archivos y el contexto disponibles en este repositorio, salvo que el desarrollador autorice expresamente fuentes externas concretas.
- La autorización debe especificar la fuente o el recurso permitido; no la extiendas a otras fuentes.
