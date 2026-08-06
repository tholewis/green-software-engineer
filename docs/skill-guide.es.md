---
title: "Revisión de software verde — Guía de la skill"
description: "Uso de /revision-verde para revisar la sostenibilidad del backend, datos, infraestructura e inteligencia artificial."
category: reference
version: "1.0.0-es"
last_updated: "2026-08-06"
audience: developers
tags: [skill, software-verde, sostenibilidad, carbono, revisión, español]
---

# Revisión de software verde — Guía de la skill

[Documentación inglesa](skill-guide.md) | [Documentación española](skill-guide.es.md)

## Requisitos previos

- Claude Code instalado y autenticado.
- El archivo `.claude/skills/revision-verde/SKILL.md` en el proyecto o en la configuración global.
- No se necesitan dependencias ni claves de API adicionales a las requeridas por Claude Code.

## Qué es una skill

Una skill es un conjunto reutilizable de instrucciones que Claude Code descubre en un
directorio `.claude/skills/`. El nombre del directorio se convierte en el comando que el
usuario puede invocar y el campo `description` ayuda a Claude a decidir cuándo cargarla.

## Qué hace `/revision-verde`

La skill convierte los principios de software verde en un control recurrente dentro del
flujo de desarrollo. Busca ineficiencias en código, arquitectura y configuración, y
propone cambios que se puedan medir y verificar.

Puede activarse automáticamente cuando Claude trabaja con:

| Tipo de trabajo | Ejemplos |
|---|---|
| APIs | Endpoints REST, resolvers GraphQL, webhooks |
| Bases de datos | SQL, consultas ORM, migraciones e índices |
| Infraestructura | Terraform, Pulumi, CloudFormation y Kubernetes |
| Procesos en segundo plano | Cron, colas y workers |
| Pipelines de datos | ETL, procesamiento por lotes o streams |
| Cachés | Estrategias de caché, TTL e invalidación |
| IA y ML | Inferencia, agentes, entrenamiento y pipelines de modelos |

No debe activarse automáticamente para cambios exclusivos de interfaz, documentación o
pruebas que no modifiquen el comportamiento de producción. Siempre puede invocarse de
forma explícita si el usuario considera que esos cambios tienen un impacto relevante.

## Invocación

```text
/revision-verde
```

También se puede añadir contexto en el mismo mensaje:

```text
/revision-verde revisa los cambios de este endpoint y su consulta SQL
```

## Categorías de revisión

### Eficiencia energética

Busca cálculos redundantes, algoritmos costosos, carga anticipada innecesaria, operaciones
intensivas en la ruta crítica y espera activa que pueda sustituirse por eventos.

### Eficiencia de red

Busca payloads sobredimensionados, datos no utilizados, viajes de ida y vuelta evitables,
compresión inadecuada y oportunidades justificadas para caché, CDN o edge.

### Cómputo y almacenamiento

Busca consultas N+1, índices ausentes, resultados sin límite, almacenamiento ineficiente,
retención indefinida y cálculos repetidos que podrían almacenarse temporalmente.

### Nube e infraestructura

Busca recursos sobredimensionados, baja utilización, servicios siempre activos,
oportunidades de escalado a cero y cargas que puedan desplazarse a regiones o momentos
con electricidad de menor intensidad de carbono.

### Hardware y carbono incorporado

Busca recursos físicos infrautilizados, oportunidades de consolidación, decisiones que
acorten innecesariamente la vida útil del hardware y cambios que solo oculten el consumo.

### IA y ML

Busca límites SCI incorrectos, unidades funcionales poco representativas, operaciones
agénticas omitidas, etapas de entrenamiento excluidas, falta de transparencia entre valores
brutos y efectivos, y baja utilización de GPU o TPU.

## Grados de severidad

| Severidad | Significado |
|---|---|
| 🔴 Alta | Impacto potencial importante y evidencia suficiente para priorizar la investigación o corrección |
| 🟡 Media | Ineficiencia relevante que merece medición y planificación próxima |
| 🟢 Baja | Mejora limitada o dependiente de condiciones que todavía deben validarse |
| ✅ Ya es sostenible | El patrón observado ya aplica correctamente una práctica de software verde |

La severidad representa impacto probable, no una cantidad de carbono demostrada. Sin una
línea base y una medición comparable, la skill debe evitar cifras o reducciones categóricas.

## Formato de cada hallazgo

```text
[PRINCIPIO] Título breve
Severidad: 🔴 Alta / 🟡 Media / 🟢 Baja
Evidencia: Elemento observado en el código, la configuración o la arquitectura.
Problema: Una frase que describa la ineficiencia y su alcance probable.
Sugerencia: Corrección concreta o alternativa.
Medición: Línea base, indicador y comparación recomendados.
Compromisos: Costos, riesgos o efectos secundarios relevantes.
```

Después de los hallazgos, la skill presenta un resumen con:

- Conteo por severidad.
- Cambio prioritario.
- Incertidumbres que deben medirse.
- Conveniencia de establecer una línea base SCI.

## Principios de evidencia

La revisión sigue estas reglas:

1. Priorizar mediciones energéticas directas.
2. Identificar expresamente cualquier indicador indirecto.
3. Comparar antes y después con el mismo método y límite del sistema.
4. Documentar región, horario, hardware, carga y unidad funcional cuando sean materiales.
5. Evaluar compromisos de rendimiento, confiabilidad, costo y mantenibilidad.
6. Evitar falsos positivos y recomendaciones genéricas sin evidencia local.

Indicadores indirectos habituales:

- Tiempo de CPU o duración total.
- Asignación y uso de memoria.
- Utilización de CPU, GPU o TPU.
- Bytes almacenados o transferidos.
- Número de consultas, solicitudes o invocaciones de modelos.

Estos indicadores pueden orientar una investigación, pero no equivalen automáticamente a
energía o emisiones de carbono.

## Agente o skill

| | Skill (`/revision-verde`) | Agente (`ingeniero-software-verde`) |
|---|---|---|
| Uso | Revisión estructurada y recurrente | Conversación, diseño y análisis profundo |
| Invocación | Automática o expresa | Expresa o por delegación |
| Contexto | Conversación principal | Ventana aislada |
| Resultado | Lista uniforme de hallazgos | Recomendación adaptable |

## Instalación

Para un solo proyecto:

```text
tu-proyecto/
└── .claude/
    └── skills/
        └── revision-verde/
            └── SKILL.md
```

Para todos los proyectos:

```text
~/.claude/skills/revision-verde/SKILL.md
```

Claude Code detecta la skill por el archivo `SKILL.md`; no se requiere un registro adicional.

## Autoría

Esta adaptación española se basa en la skill creada por Thomas Lewis en
[`tholewis/green-software-engineer`](https://github.com/tholewis/green-software-engineer).
La traducción y revisión son mantenidas por Interdato Sostenibilidad Digital.

## Referencias

- [Formación de software verde en español](https://learn.greensoftware.foundation/es/)
- [Patrones de software verde](https://patterns.greensoftware.foundation)
- [Especificación SCI](https://sci.greensoftware.foundation)
- [Especificación SCI for AI](https://github.com/Green-Software-Foundation/sci-ai/blob/dev/SPEC.md)
- [Documentación de skills de Claude Code](https://code.claude.com/docs/es/skills)
