# Brasaland — Technical Context

**Estado:** Descubrimiento / plantilla inicial  
**Última actualización:** 2026-10-17  
**Alcance:** Inventario de la configuración y las convenciones documentadas en este repositorio. No describe una plataforma de producción ni una arquitectura aprobada para Brasaland.

## 1. Resumen

El repositorio está en una fase de plantilla y documentación. Contiene una configuración de entorno de desarrollo, un paquete TypeScript con tipos de ejemplo, un script Python de limpieza de datos y guías para organizar futuras aplicaciones y servicios. No se identifica una aplicación empresarial ejecutable ni una arquitectura de despliegue implantada.

En este documento se diferencia entre:

- **Configurado/presente:** artefactos encontrados en el repositorio.
- **Recomendado:** orientación de las guías de la plantilla, todavía no implementada.
- **Pendiente:** decisiones o componentes que no se encontraron y que requerirían definición.

## 2. Entorno de desarrollo configurado

La configuración en [`.devcontainer/devcontainer.json`](../.devcontainer/devcontainer.json) declara:

- Imagen base de Dev Container: Ubuntu 24.04.
- Python 3.12, con instalación de JupyterLab.
- Node.js 22.
- Docker «outside of Docker», GitHub CLI y SSH.
- Extensiones de VS Code para Python/Pylance, Jupyter, Docker, Prettier, ESLint, Error Lens y GitLens, entre otras.
- Reenvío de puertos 3000, 8000 y 5678.
- Configuración condicional al crear el contenedor: habilita Corepack y pnpm, ejecutando `pnpm install` si hay un `package.json` en la raíz; actualiza pip e instala `uv`, ejecutando `uv sync` si hay un `pyproject.toml` en la raíz.

Esta sección documenta lo que la configuración declara; no verifica por sí sola la instalación efectiva de cada herramienta ni define el entorno de producción.

## 3. Tecnologías y código presentes

### TypeScript — tipos compartidos de ejemplo

Existe el paquete privado [`@repo/shared-types`](../packages/shared/package.json), versión `0.0.1`, con `main` y `types` apuntando a `index.ts` y sin scripts declarados. [`packages/shared/types/index.ts`](../packages/shared/types/index.ts) define `Id` y `BaseEntity` como ejemplos ampliables.

El repositorio no demuestra que el paquete esté consumido por aplicaciones ni que exista un workspace/runner en la raíz. La guía principal también indica que no hay un runner de workspace configurado.

### Python y pandas — script de ejemplo

[`skills/data-analysis/scripts/pandas_clean.py`](../skills/data-analysis/scripts/pandas_clean.py) contiene un ejemplo de limpieza de CSV que importa pandas. Es un script de referencia dentro de una skill, no evidencia de un pipeline de producción ni de dependencias instaladas y declaradas para la aplicación.

### Herramientas mencionadas, no implementadas como stack de producto

La guía menciona FastAPI para el backend y Docker, n8n, Streamlit y Gradio como opciones o ejemplos de organización/uso. No se encontraron implementaciones de servicios, flujos o aplicaciones que permitan afirmar que estas tecnologías hayan sido seleccionadas para Brasaland.

## 4. Convenciones y recomendaciones de arquitectura

La plantilla organiza el monorepo por responsabilidades ([`README.md`](../README.md)):

- `uis/`: interfaces de usuario.
- `services/`: APIs y workers.
- `data/`: datos, pipelines y evaluación.
- `agents/`, `skills/`, `mcps/`: capacidades de IA y herramientas relacionadas.
- `workflows/`: automatización y orquestación.
- `packages/`: librerías compartidas versionables.
- `shared/`: recursos comunes ligeros.
- `infra/`, `scripts/`, `internal/`: infraestructura, automatización pequeña y herramientas internas.
- `docs/`: arquitectura, decisiones y convenciones transversales.

La guía recomienda comenzar con **una API centralizada FastAPI** y evitar microservicios al inicio; añadir módulos/routers por dominio y extraer workers solo cuando sea necesario. Es orientación de la plantilla, no una arquitectura ejecutada ni una decisión aprobada para el proyecto.

También se recomienda que cada aplicación, servicio, agente o pipeline tenga una subcarpeta y documentación propia. No se encontraron ADRs que formalicen decisiones de arquitectura en `docs/`.

## 5. Estado de implementación y decisiones pendientes

Según la guía del repositorio y el inventario de archivos realizado para este documento:

- El repositorio se presenta como estructura base y documentación, sin aplicaciones ejecutables o scripts globales en la raíz.
- No hay un `package.json` ni `pyproject.toml` de raíz entre los archivos identificados, por lo que los comandos condicionales de instalación del Dev Container no configuran un proyecto raíz.
- No se encontró un runner de workspace en la raíz.
- No se identificaron un backend/API implementado, interfaz de producto, base de datos, sistema de colas, proveedor de modelos, infraestructura de producción ni configuración de CI/CD.
- No se localizó `docker-compose.yml` en la raíz; la guía lo propone como ubicación recomendada para orquestación local futura.
- No se encontraron ADRs bajo `docs/`; su directorio contiene actualmente guías README.

Estas observaciones describen el estado inspeccionado del repositorio, y no afirman que la empresa carezca de sistemas externos fuera de él.

## 6. Restricciones y consideraciones técnicas del dominio

El briefing empresarial en [`CONTEXT.md`](../CONTEXT.md) describe:

- 14 locales en Colombia y Florida y sistemas POS distintos por país, sin integración descrita.
- Procesos actuales apoyados en hojas de cálculo, WhatsApp, teléfono e informes periódicos.
- Necesidad de consolidar datos de varios locales y países; ventas y reporting deben considerar COP y USD.
- Español e inglés como idiomas relevantes para la operación y la formación.
- Diferencias entre los contextos laborales de Colombia y Florida para cualquier solución de RR. HH.

Estas condiciones implican que las integraciones, la normalización de datos, los husos horarios/monedas, los permisos por país y la calidad de los datos deberán descubrirse y diseñarse antes de implementar. Son consideraciones, no requisitos técnicos detallados ni decisiones ya tomadas.

La propuesta de personalización de menú de [`company-choice.md`](../company-choice.md) es una idea exploratoria del estudiante, no un alcance aprobado. Si se desarrolla, deberán definirse el consentimiento y uso opcional del historial, la minimización y retención de datos, y el tratamiento seguro de preferencias y datos de alergias/intolerancias. La recomendación de IA no debe sustituir información autoritativa sobre alérgenos ni la orientación del personal. No se ha realizado aquí una evaluación legal o de seguridad.

## 7. Decisiones técnicas aún no tomadas

No hay evidencia en los archivos inspeccionados de elecciones aprobadas para:

- Framework de frontend o arquitectura de interfaces.
- Base de datos o estrategia de almacenamiento.
- API implementada, autenticación o autorización.
- Protocolo/formato de integración con los POS.
- Infraestructura de producción, cloud o despliegue.
- Proveedor/modelo de IA, estrategia RAG o plataforma de agentes.
- Colas, mensajería, observabilidad, CI/CD o política de pruebas.

Deben tratarse como decisiones pendientes de descubrimiento y priorización; no completar estos puntos suponiendo que una opción citada en una guía ya fue adoptada.

## 8. Fuentes

- [`.devcontainer/devcontainer.json`](../.devcontainer/devcontainer.json) — herramientas y configuración de desarrollo.
- [`README.md`](../README.md) — estado de la plantilla, convenciones del monorepo y recomendación para `services/`.
- [`services/README.md`](../services/README.md) — documentación esperada para servicios futuros.
- [`packages/shared/package.json`](../packages/shared/package.json) y [`packages/shared/types/index.ts`](../packages/shared/types/index.ts) — metadata y tipos compartidos de ejemplo.
- [`skills/data-analysis/scripts/pandas_clean.py`](../skills/data-analysis/scripts/pandas_clean.py) — ejemplo Python/pandas.
- [`CONTEXT.md`](../CONTEXT.md) — contexto de sistemas y operación de Brasaland.
- [`company-choice.md`](../company-choice.md) — intereses del estudiante e idea de personalización.
- [`projectbrief.md`](./projectbrief.md) — encuadre de negocio y límites de alcance.
