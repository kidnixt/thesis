Técnica experimental de alto rendimiento que mide el efecto de miles de mutaciones en una proteína sobre su función/estabilidad/fitness de forma simultánea.

## Concepto

En lugar de hacer mutaciones una por una, DMS:
1. Genera una colección masiva de variantes (miles-millones)
2. Somete todas a una presión selectiva (binding, estabilidad, etc.)
3. Usa deep sequencing para cuantificar qué variantes sobreviven

Resultado: para cada posición de la proteína, se obtiene el fitness de todas ~20 mutaciones naturales.

## Proceso típico

1. **Mutagénesis**: generar biblioteca de variantes (usando error-prone PCR, etc.)
2. **Selección**: exponer a presión selectiva (binding, enzymatic activity, etc.)
3. **Deep sequencing**: determinar abundancia relativa de cada variante
4. **Scoring**: calcular fitness = log(abundancia_post / abundancia_pre)

## Ventajas

- **Escala masiva**: miles de mutaciones en un experimento
- **Rápido**: resultados en semanas (vs años si hacer una por una)
- **Cuantitativo**: produce scores numéricos de fitness
- **Costo-efectivo**: una sola ronda de selección = datos masivos

## Datasets benchmark

En el paper, se utilizan proteínas famosas con datos DMS:
- **TEM-1 β-lactamase**: resistencia a antibióticos
- **Influenza hemagglutinin**: viral fitness
- **Ubiquitin**: estabilidad
- **GFP**: fluorescencia
- **HSP90**: chaperone protein

## Limitaciones

- **Dependiente de presión selectiva**: solo mide fitness bajo condición específica
- **Artifacts experimentales**: puede haber bias en selección
- **Contexto limitado**: no mide todas las propiedades simultáneamente
- **Proteína específica**: cada DMS es un experimento separado

## En el paper de Language Models

El paper valida el modelo de language modeling contra datasets DMS de 5 proteínas diferentes.

Resultados:
- PLM grande supera o iguala métodos como [[SIFT|SIFT]], [[EVMutation|EVMutation]], [[DeepSequence|DeepSequence]]
- **Sin necesidad de entrenar un modelo por proteína**
- **Sin necesidad de construir MSA**

Métrica: correlación entre score predicho y fitness experimental real.

## Cambio paradigmático

Antes: "diseña un modelo para cada familia de proteínas, valida con DMS"
Después: "entrena un modelo generalista, generaliza a proteínas nuevas"

Los datos DMS fueron fundamentales para demostrar que este cambio era válido.
