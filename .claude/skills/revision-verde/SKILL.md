---
name: revision-verde
description: >
  Revisa código, arquitectura y configuración según prácticas de software verde
  alineadas con la Green Software Foundation. Usar al crear o revisar endpoints de API,
  consultas de bases de datos, infraestructura o configuración cloud, tareas en segundo
  plano, pipelines de datos, cachés y cargas de IA o ML. También se puede invocar
  explícitamente con /revision-verde. No activar automáticamente para cambios exclusivos
  de interfaz, documentación o pruebas que no alteren el comportamiento en producción.
---

# Revisión de software verde

Realiza una revisión de sostenibilidad basada en los principios de la Green Software
Foundation (GSF). Identifica ineficiencias de carbono, energía y hardware, y propone
mejoras concretas y verificables.

Responde en español, salvo que el usuario solicite otro idioma. Conserva siglas y nombres
oficiales como GSF, SCI, SCI for AI, API, CDN y PUE.

## Método de revisión

1. Determinar el límite del sistema y la unidad de trabajo afectada.
2. Revisar únicamente las categorías pertinentes al cambio.
3. Separar los problemas observados de las hipótesis que requieren medición.
4. Evaluar posibles efectos fuera del componente local antes de recomendar un cambio.
5. Proponer una forma de medir el resultado cuando no exista evidencia directa.
6. No inventar hallazgos para completar la lista.

## Lista de comprobación

### ⚡ Eficiencia energética

- [ ] ¿Existen bucles intensivos o cálculos costosos que se puedan reducir, agrupar o aplazar?
- [ ] ¿Se realiza anticipadamente trabajo que podría ejecutarse bajo demanda?
- [ ] ¿Se evitan operaciones costosas —criptografía, imágenes o inferencia— en la ruta crítica cuando es posible?
- [ ] ¿Se utiliza polling inactivo cuando sería viable un mecanismo dirigido por eventos?
- [ ] ¿Se puede demostrar el beneficio con energía medida o con un indicador indirecto claramente identificado?

### 🌐 Eficiencia de red

- [ ] ¿Se minimiza el payload mediante paginación, selección de campos o compresión apropiada?
- [ ] ¿Se transfieren datos que el consumidor no necesita?
- [ ] ¿Se pueden evitar viajes de ida y vuelta mediante agrupación u otro diseño adecuado?
- [ ] ¿El contenido estático o reutilizable aprovecha caché, CDN o edge cuando corresponde?
- [ ] ¿La estrategia evita trasladar el costo a otra parte del sistema sin reducir el impacto total?

### 🗄️ Cómputo y almacenamiento

- [ ] ¿Las consultas están optimizadas, indexadas y limitadas, sin patrones N+1?
- [ ] ¿La caché evita trabajo redundante sin introducir una retención o invalidación desproporcionada?
- [ ] ¿El formato de almacenamiento es adecuado y se comprime cuando aporta beneficios?
- [ ] ¿Los datos cuentan con políticas justificadas de retención, archivo y eliminación?
- [ ] ¿Se incluyen en el análisis los costos de observabilidad, copias de seguridad y redundancia?

### ☁️ Nube e infraestructura

- [ ] ¿Los recursos están dimensionados según la carga real?
- [ ] ¿La carga puede escalar a cero o suspenderse cuando está inactiva?
- [ ] ¿La región y el horario consideran la intensidad de carbono y los requisitos de latencia o residencia de datos?
- [ ] ¿Las cargas interrumpibles pueden utilizar instancias spot o preemptibles?
- [ ] ¿Los trabajos flexibles pueden desplazarse a periodos con electricidad de menor intensidad de carbono?
- [ ] ¿Se mide la utilización antes de migrar entre servicios administrados, serverless y máquinas virtuales?

### 🔋 Hardware y carbono incorporado

- [ ] ¿El hardware está bien utilizado o permanece encendido con una carga reducida?
- [ ] ¿La consolidación permitiría utilizar menos recursos físicos sin degradar la confiabilidad?
- [ ] ¿La decisión prolonga la vida útil del hardware o evita adquisiciones innecesarias?
- [ ] ¿Un servicio administrado reduce realmente los recursos asignados, en lugar de ocultar su consumo?

### 🤖 Cargas de IA y ML

Omitir esta categoría cuando el sistema no contenga componentes de IA o ML.

- [ ] ¿Se ha definido si la medición corresponde al límite del consumidor, al proveedor o a ambos?
- [ ] ¿La unidad funcional representa cómo se entrega o escala el servicio?
- [ ] Para IA agéntica, ¿se contabilizan modelos auxiliares, herramientas, recuperación e intercambios entre modelos?
- [ ] Para entrenamiento, ¿se incluyen todas las etapas, ejecuciones intermedias y detención temprana?
- [ ] ¿Se declara si los parámetros, tokens o FLOPs son valores brutos o efectivos?
- [ ] ¿GPU y TPU mantienen una utilización adecuada entre lotes?
- [ ] ¿Se ha considerado un modelo más pequeño, menos llamadas o menor volumen de contexto sin degradar el resultado requerido?

Unidades funcionales habituales:

- LLM: por token.
- IA agéntica: por ejecución de flujo de trabajo.
- Generación de imágenes: por imagen.
- Generación de video: por segundo.
- Clasificación o ML clásico: por inferencia.
- Reconocimiento de voz: por segundo de audio procesado.
- Entrenamiento del proveedor: por FLOP, token de entrenamiento o parámetro.

## Evidencia y medición

Priorizar mediciones directas de energía y carbono. Si no están disponibles, se pueden
usar duración, tiempo de CPU, asignación de memoria, utilización del hardware o bytes
transferidos como indicadores indirectos. Nombrar siempre el indicador, explicar su
relación esperada con la energía y declarar sus limitaciones.

No afirmar que una ejecución más rápida o un payload menor reduce automáticamente el
carbono. Considerar la intensidad de carbono, el hardware, el efecto rebote y los cambios
en otros componentes del sistema.

## Formato de salida

Para cada hallazgo, producir:

```text
[PRINCIPIO] Título breve
Severidad: 🔴 Alta / 🟡 Media / 🟢 Baja
Evidencia: Elemento observado en el código, la configuración o la arquitectura.
Problema: Una frase que describa la ineficiencia y su alcance probable.
Sugerencia: Corrección concreta o alternativa.
Medición: Línea base, indicador y comparación recomendados.
Compromisos: Costos, riesgos o efectos secundarios relevantes.
```

Cerrar con una sección **Resumen** que incluya:

- Total de hallazgos por severidad.
- El cambio prioritario con mayor potencial de reducción.
- Incertidumbres que requieren medición.
- Si conviene establecer una línea base SCI.

Si el código ya está bien optimizado, indicarlo expresamente. Los falsos positivos reducen
la confianza y pueden provocar cambios que aumenten el impacto total.

## Referencias

- Formación de software verde en español: https://learn.greensoftware.foundation/es/
- Patrones de software verde: https://patterns.greensoftware.foundation
- Especificación SCI: https://sci.greensoftware.foundation
- Especificación SCI for AI: https://github.com/Green-Software-Foundation/sci-ai/blob/dev/SPEC.md
