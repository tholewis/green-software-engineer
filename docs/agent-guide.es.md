---
title: "Ingeniero de software verde — Guía del agente"
description: "Uso de ingeniero-software-verde para revisiones de sostenibilidad, arquitectura consciente del carbono y medición SCI."
category: reference
version: "1.0.0-es"
last_updated: "2026-08-06"
audience: developers
tags: [agente, software-verde, sostenibilidad, SCI, carbono, español]
---

# Ingeniero de software verde — Guía del agente

[Documentación inglesa](agent-guide.md) | [Documentación española](agent-guide.es.md)

## Requisitos previos

- Claude Code instalado y autenticado.
- El archivo `.claude/agents/ingeniero-software-verde.md` en la raíz del proyecto o en `~/.claude/agents/`.
- No se necesitan dependencias ni claves de API adicionales a las requeridas por Claude Code.

## Qué es un agente

En Claude Code, un agente personalizado es una instancia especializada con su propia ventana
de contexto e instrucciones. Se puede invocar expresamente mediante una mención y Claude
también puede delegarle una tarea cuando la descripción del agente coincide con el trabajo.

## Qué hace este agente

`ingeniero-software-verde` funciona como consultor de sostenibilidad dentro del flujo de desarrollo.
Analiza decisiones de código y arquitectura con base en los principios de la Green Software
Foundation, la especificación SCI y los patrones de software verde.

| Caso | Ejemplo |
|---|---|
| Evaluar una decisión de arquitectura | `@agent-ingeniero-software-verde compara estas dos arquitecturas` |
| Revisar código | `@agent-ingeniero-software-verde revisa este endpoint para detectar puntos críticos de carbono` |
| Definir una medición SCI | `@agent-ingeniero-software-verde ayúdame a definir el límite y la unidad funcional` |
| Comparar mecanismos | `@agent-ingeniero-software-verde compara polling y WebSockets` |
| Auditar infraestructura | `@agent-ingeniero-software-verde busca sobreaprovisionamiento en este Terraform` |

## Idioma y terminología

El agente responde en español por defecto y conserva las siglas oficiales. La terminología
principal sigue la traducción española de la formación de la Green Software Foundation:

| Inglés | Español utilizado |
|---|---|
| Green software | Software verde |
| Carbon efficiency | Eficiencia de carbono |
| Energy efficiency | Eficiencia energética |
| Carbon awareness | Conciencia sobre el carbono |
| Carbon intensity | Intensidad de carbono |
| Embodied carbon | Carbono incorporado |
| Hardware efficiency | Eficiencia del hardware |
| Energy proportionality | Proporcionalidad energética |
| Demand shifting | Cambio o desplazamiento de la demanda |
| Demand shaping | Adaptación de la demanda |
| Functional unit | Unidad funcional |

## Conocimiento del agente

### Principios y áreas de la GSF

El proyecto fuente utiliza los ocho principios originales: carbono, electricidad,
intensidad de carbono, carbono incorporado, proporcionalidad energética, redes,
adaptación de la demanda, y medición y optimización.

La formación actual de la GSF los organiza en seis áreas: eficiencia de carbono,
eficiencia energética, conciencia sobre el carbono, eficiencia del hardware, medición y
compromisos climáticos. El agente conoce ambas clasificaciones y puede indicar cuál aplica.

### Fórmula SCI

La Intensidad de Carbono del Software (Software Carbon Intensity, SCI) es una tasa de
emisiones por unidad funcional:

```text
SCI = ((E × I) + M) / R
```

| Variable | Significado | Unidad típica |
|---|---|---|
| `E` | Energía consumida por el sistema | kWh |
| `I` | Intensidad de carbono de la electricidad de la región | gCO₂eq/kWh |
| `M` | Emisiones incorporadas asignadas al hardware utilizado | gCO₂eq |
| `R` | Unidad funcional que describe cómo escala el sistema | solicitud, usuario, transacción, ejecución |

El agente puede ayudar a:

- Delimitar los componentes incluidos en la medición.
- Seleccionar una unidad funcional significativa.
- Distinguir datos medidos de valores modelados.
- Diseñar una línea base y una comparación después del cambio.
- Documentar suposiciones, fuentes y limitaciones.

### SCI for AI

Para sistemas de IA, SCI for AI distingue:

| Perspectiva | Etapas principales | Ejemplos de unidad funcional |
|---|---|---|
| Consumidor | Operación y monitoreo: inferencia, API, orquestación, observabilidad, almacenamiento y UX | Por token, ejecución de flujo, imagen, segundo o inferencia |
| Proveedor | Concepción, diseño y desarrollo, despliegue y retirada | Por FLOP, token de entrenamiento o parámetro |

Las mediciones de IA agéntica deben considerar las operaciones desencadenadas por el flujo,
no solo la llamada principal al modelo. Las mediciones de entrenamiento deben cubrir la
ejecución completa, incluidas pruebas intermedias y detención temprana.

## Cómo invocar el agente

```text
@agent-ingeniero-software-verde <pregunta, archivo o tarea>
```

También se puede escribir `@`, seleccionar `ingeniero-software-verde (agent)` en el menú y
añadir la tarea. Se puede mencionar un archivo, pegar código o formular una pregunta conceptual.
Como el agente trabaja en un contexto aislado, conviene incluir el objetivo del sistema,
el volumen de carga y las restricciones que afecten la recomendación.

Para una revisión más útil, proporcionar cuando sea posible:

- Región y proveedor de infraestructura.
- Patrón de tráfico y objetivos de latencia.
- Recursos asignados y utilización observada.
- Tamaño de datos y frecuencia de transferencia.
- Métricas disponibles de energía, CPU, memoria o red.
- Unidad funcional que importa al negocio.

## Agente o skill

| | Agente (`ingeniero-software-verde`) | Skill (`/revision-verde`) |
|---|---|---|
| Uso | Preguntas, arquitectura y auditorías exhaustivas | Revisión recurrente de cambios |
| Invocación | Expresa o por delegación | Automática o expresa |
| Contexto | Aislado | Conversación principal |
| Salida | Consultiva y adaptable | Hallazgos estructurados |

## Ubicación del archivo

Proyecto específico:

```text
tu-proyecto/
└── .claude/
    └── agents/
        └── ingeniero-software-verde.md
```

Disponibilidad global:

```text
~/.claude/agents/ingeniero-software-verde.md
```

## Limitaciones

- Una recomendación no demuestra por sí sola una reducción de carbono.
- El tiempo de ejecución, la memoria y los bytes transferidos son indicadores indirectos,
  no mediciones energéticas equivalentes.
- La intensidad de carbono cambia según la región y el momento.
- Una optimización local puede desplazar el impacto a otra parte del sistema.
- Las comparaciones SCI necesitan límites, unidades funcionales y metodologías coherentes.

## Autoría

Esta adaptación española se basa en el agente creado por Thomas Lewis en
[`tholewis/green-software-engineer`](https://github.com/tholewis/green-software-engineer).
La traducción y revisión son mantenidas por Interdato Sostenibilidad Digital.

## Referencias

- [Green Software Foundation](https://greensoftware.foundation)
- [Formación de software verde en español](https://learn.greensoftware.foundation/es/)
- [Patrones de software verde](https://patterns.greensoftware.foundation)
- [Especificación SCI](https://sci.greensoftware.foundation)
- [Especificación SCI for AI](https://github.com/Green-Software-Foundation/sci-ai/blob/dev/SPEC.md)
- [Documentación de agentes de Claude Code](https://code.claude.com/docs/en/sub-agents)
