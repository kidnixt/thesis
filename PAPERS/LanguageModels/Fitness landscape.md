Representación conceptual del espacio de todas las posibles secuencias de una proteína, donde cada punto tiene asociado un valor de fitness (función biológica). La "landscape" es una hipersuperficie multidimensional.

## Concepto visual

Imagina un mapa de altitud donde:
- **Ejes**: dimensiones de variación secuencial
- **Altura**: fitness de esa secuencia
- **Picos**: óptimos locales o globales
- **Valles**: secuencias de bajo fitness

Una mutación es un movimiento en ese landscape.

## Propiedades importantes

### Rugosidad
- **Landscape liso**: cambios pequeños en secuencia → cambios predecibles en fitness
- **Landscape rugoso**: cambios caóticos, epistasis complicada

La mayoría de proteínas tienen landscapes rugosos.

### Accesibilidad
- Desde un punto, ¿se puede alcanzar un óptimo mejor?
- Depende de [[Epistasis|epistasis]] local

## [[Epistasis]]

En una landscape rugosa:
- Una mutación puede ser deleterious en contexto A
- Pero beneficiosa en contexto B
- Esto es [[Epistasis|epistasis]]: el efecto de una mutación depende del background

## En evolución

La evolución camina en el landscape:
- Parte de una secuencia ancestral
- Sigue gradientes de fitness
- Queda atrapada en óptimos locales (no puede cruzar valles de bajo fitness)

## En el paper de Language Models

El paper sugiere que modelos entrenados en evolución natural aprenden la **estructura del fitness landscape**:

> "modelos grandes empiezan a capturar [...] fitness landscapes"

Esto implica que:
- El modelo aprende dónde están los picos
- Aprende cómo se conectan regiones de alto fitness
- Puede predecir fitness sin observar experimentalmente

Sin mediciones experimentales, solo observando 250M secuencias evolutivas.

## Cómo [[Zero-shot prediction]] trabaja

Un language model que entiende el fitness landscape puede:
- Dar una mutación nueva
- Predecir si cae en un pico o un valle
- Sin entrenamiento específico en esa proteína

Porque el landscape es similar entre proteínas relacionadas.

## Desafíos

- **Extremadamente alta dimensional**: proteína de 300aa = 300×20 dimensiones (~6000D)
- **Imposible visualizar**: no se puede graficar en 2D/3D
- **Contextual**: el landscape cambia con presión selectiva (ambiente)

## En drug discovery

En DrugLLM, la idea es similar: optimizar moléculas caminando en un landscape de [[SAR|SAR]]:
- Cada molécula es un punto
- Fitness = propiedades farmacológicas
- [[NMP|NMP]] aprende cómo caminar en ese landscape

## Conexión conceptual

- **Protein folding**: landscape de conformaciones
- **Protein evolution**: landscape de secuencias y fitness
- **Molecular design**: landscape de moléculas y propiedades

Language models implícitamente aprenden estas landscapes.
