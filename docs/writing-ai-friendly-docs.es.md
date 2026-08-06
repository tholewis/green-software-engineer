# Cómo escribir documentación accesible para sistemas de IA

Esta guía establece criterios para producir documentación útil tanto para personas como
para sistemas de inteligencia artificial.

## Estructura y semántica

- Usar encabezados descriptivos y coherentes.
- Preferir secciones modulares y poco profundas.
- Emplear marcado semántico y metadatos estructurados cuando corresponda.
- Hacer que cada sección responda a una pregunta concreta.

## Claridad

- Definir siglas y términos la primera vez que aparezcan.
- Escribir con lenguaje directo y evitar expresiones ambiguas.
- Declarar requisitos previos, resultados y supuestos.
- Indicar versiones y condiciones del entorno cuando sean relevantes.

## Ejemplos de código

- Proporcionar ejemplos ejecutables y fáciles de copiar.
- Especificar el lenguaje en cada bloque de código.
- Comentar únicamente las partes que no sean evidentes.
- Mostrar la llamada y el resultado esperado en los ejemplos de API.

## Formatos legibles por máquinas

- Utilizar OpenAPI u otro esquema adecuado para documentar APIs.
- Usar JSON, YAML u otros formatos estructurados para metadatos.
- Mantener un archivo `llms.txt` que resuma la documentación y sus rutas.

## Navegación

- Incluir un índice con una descripción breve de cada documento.
- Usar enlaces internos coherentes y URLs canónicas.
- Evitar que información imprescindible aparezca solamente en imágenes.

## Metadatos y contexto

- Añadir título, descripción, categoría, versión y fecha de actualización a los documentos técnicos.
- Identificar la audiencia y el caso de uso.
- Evitar contenido cuya versión o vigencia no pueda determinarse.

> Principio central: escribir primero para las personas, con suficiente precisión para que
> una máquina pueda reconstruir el significado sin depender de contexto implícito.
