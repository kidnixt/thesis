Representación numérica (vector) de una [[Proteína]] generada por un [[Modelo de lenguaje de proteínas]].

## ¿Qué es un embedding?

Un embedding es:
- Un vector de números (típicamente 256-2560 dimensiones)
- Una representación comprimida de la información de la proteína
- La "visión" que el modelo tiene de esa proteína

## Tipos de embeddings

### Por residuo
- Un vector por cada [[Aminoácido]]
- Útil para predicciones a nivel de posición
- Ejemplo: predicción de [[Estructura de proteínas|estructura secundaria]]

### Por proteína
- Un vector para toda la [[Secuencia de aminoácidos]]
- Útil para clasificación o comparación
- Se obtiene promediando o pooling de embeddings por residuo

## Propiedades

Los embeddings capturan:
- Similitud de [[Función de proteínas|función]]
- Relaciones evolutivas ([[Familia de proteínas]])
- Propiedades como [[Estabilidad proteica]], [[Solubilidad de proteínas|solubilidad]]

Proteínas similares tienen embeddings similares (cercanos en el espacio vectorial).

## Aplicaciones

- **Clasificación**: entrada para clasificadores de [[Anotación funcional]]
- **Clustering**: agrupar proteínas similares
- **Búsqueda**: encontrar proteínas relacionadas
- **Transfer learning**: base para modelos específicos

## En SaProt

SaProt genera embeddings que incorporan información estructural, lo que los hace más informativos que embeddings basados solo en secuencia.

Ver [[SAPROT/TUTORIAL|Tutorial de SaProt]] — los embeddings son la base de todas las tareas de clasificación y regresión.