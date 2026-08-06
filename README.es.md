![Software verde con IA](docs/green-software-with-ai.jpeg)

[English](README.md) | [Español](README.es.md)

# Ingeniero de software verde para Claude Code

Un agente y una skill de Claude Code que integran prácticas de sostenibilidad de la
[Green Software Foundation](https://greensoftware.foundation) directamente en el flujo de desarrollo.

Esta edición española adapta el trabajo original de
[Thomas Lewis](https://github.com/tholewis), publicado en
[`tholewis/green-software-engineer`](https://github.com/tholewis/green-software-engineer).
La traducción y revisión en español son mantenidas por
[Interdato Sostenibilidad Digital](https://github.com/Interdato-SostenibilidadDigital).

---

## Contenido

| Archivo | Tipo | Propósito |
|---|---|---|
| `.claude/agents/ingeniero-software-verde.md` | **Agente** | Consultor de sostenibilidad para preguntas, arquitectura y auditorías exhaustivas de código |
| `.claude/skills/revision-verde/SKILL.md` | **Skill** | Revisión de software verde que puede activarse automáticamente al escribir código de backend |

La versión inglesa original permanece disponible en los archivos indicados en
[`README.md`](README.md).

---

## Documentación

| Página | Descripción |
|---|---|
| [Guía del agente](docs/agent-guide.es.md) | Cómo invocar `@agent-ingeniero-software-verde`, casos de uso y base de conocimiento |
| [Guía de la skill](docs/skill-guide.es.md) | Cómo funciona `/revision-verde`, reglas de activación, categorías y formato de salida |

---

## Inicio rápido

### Requisitos previos

- **Claude Code** actualizado, disponible como CLI, aplicación de escritorio o extensión para IDE.
- Una suscripción de Claude Code; no se necesitan claves de API adicionales.

### 1. Copiar los archivos españoles en el proyecto

```text
tu-proyecto/
└── .claude/
    ├── agents/
    │   └── ingeniero-software-verde.md
    └── skills/
        └── revision-verde/
            └── SKILL.md
```

Para utilizarlos en **todos** los proyectos, se pueden copiar en la configuración global:

```text
~/.claude/
├── agents/
│   └── ingeniero-software-verde.md
└── skills/
    └── revision-verde/
        └── SKILL.md
```

### 2. Abrir el proyecto en Claude Code

```bash
claude
```

### 3. Utilizarlos

**Consultar al agente:**

```text
@agent-ingeniero-software-verde ¿cuál es la forma más sostenible de gestionar cargas de imágenes a escala?
```

**Ejecutar una revisión explícita:**

```text
/revision-verde
```

**Permitir la activación automática:** al trabajar con endpoints de API, consultas de bases
de datos, infraestructura en la nube, tareas en segundo plano, pipelines de datos o cachés,
Claude puede cargar la skill cuando la considere pertinente.

---

## Agente: `ingeniero-software-verde`

Un agente especializado en ingeniería de software verde, fundamentado en:

- Los principios y áreas de conocimiento de la **Green Software Foundation**.
- La especificación **SCI (ISO/IEC 21031:2024)**: `SCI = ((E × I) + M) / R`.
- Los [patrones de software verde](https://patterns.greensoftware.foundation).
- La especificación **SCI for AI** para sistemas de inteligencia artificial.

Ejemplos:

```text
@agent-ingeniero-software-verde revisa este endpoint para detectar ineficiencias de carbono
@agent-ingeniero-software-verde ayúdame a calcular el SCI de este servicio
@agent-ingeniero-software-verde compara polling y WebSockets desde la perspectiva de sostenibilidad
@agent-ingeniero-software-verde audita esta configuración de Terraform por sobreaprovisionamiento
```

Más información en la [guía del agente](docs/agent-guide.es.md).

---

## Skill: `/revision-verde`

Una revisión estructurada de sostenibilidad que cubre:

- ⚡ **Eficiencia energética:** bucles, carga diferida, trabajo redundante y polling.
- 🌐 **Eficiencia de red:** tamaño de payloads, viajes de ida y vuelta, compresión y CDN.
- 🗄️ **Cómputo y almacenamiento:** consultas, cachés, formatos y retención de datos.
- ☁️ **Nube e infraestructura:** aprovisionamiento, escalado a cero, regiones y desplazamiento temporal.
- 🔋 **Hardware y carbono incorporado:** utilización y ciclo de vida del hardware.
- 🤖 **Cargas de IA y ML:** límites de medición, unidades funcionales y utilización de aceleradores.

Clasificación de los hallazgos: 🔴 Alto / 🟡 Medio / 🟢 Bajo / ✅ Ya es sostenible.

Más información en la [guía de la skill](docs/skill-guide.es.md).

---

## Agente o skill

| | Agente | Skill |
|---|---|---|
| Invocación | Seleccionar el agente con `@` o escribir `@agent-ingeniero-software-verde` | Automática o `/revision-verde` |
| Uso recomendado | Consultas, arquitectura y auditorías exhaustivas | Control recurrente mientras se programa |
| Contexto | Ventana de contexto aislada | Conversación principal |
| Salida | Conversacional y consultiva | Lista estructurada de hallazgos |

---

## Autoría y atribución

- **Trabajo original:** Thomas Lewis — [`tholewis/green-software-engineer`](https://github.com/tholewis/green-software-engineer).
- **Traducción y adaptación al español:** Interdato Sostenibilidad Digital.
- Esta adaptación mantiene las referencias técnicas y el propósito del proyecto original.
- El repositorio original no contiene actualmente un archivo de licencia. No se añade ni se presupone una licencia en esta adaptación; las condiciones de redistribución deberán ser confirmadas por el autor original.

---

## Referencias

- [Green Software Foundation](https://greensoftware.foundation)
- [Curso de software verde en español](https://learn.greensoftware.foundation/es/)
- [Catálogo de patrones de software verde](https://patterns.greensoftware.foundation)
- [Especificación SCI](https://sci.greensoftware.foundation)
- [Especificación SCI for AI](https://github.com/Green-Software-Foundation/sci-ai/blob/dev/SPEC.md)
