Representación conceptual de todas las [[Proteína]]s posibles y sus relaciones en términos de [[Secuencia de aminoácidos|secuencia]], [[Estructura de proteínas|estructura]] y [[Función de proteínas|función]].

## Concepto multidimensional

El espacio de proteínas es una abstracción que incluye múltiples perspectivas:

### Espacio de secuencias
→ Ver [[Espacio de secuencias proteicas]]

### Espacio de estructuras
- Proteínas con secuencias diferentes pueden tener estructuras similares
- El espacio de estructuras es más pequeño que el de secuencias
- Las estructuras se agrupan en "folds" característicos

### Espacio de funciones
- Aún más pequeño: muchas estructuras → pocas funciones
- Las funciones se pueden organizar jerárquicamente (Gene Ontology)

## Navegando el espacio

- **Evolución natural**: explora el espacio lentamente por [[Mutación]]
- **[[Diseño de proteínas]]**: intenta saltar a regiones nuevas
- **[[Modelo de lenguaje de proteínas]]**: aprenden la "geometría" del espacio

## En modelos computacionales

Los PLMs aprenden una representación implícita del espacio de proteínas:
- Las predicciones **zero-shot** evalúan si una variante "tiene sentido" en este espacio
- El modelo distingue secuencias "plausibles" de "absurdas"

Ver [[SAPROT/TUTORIAL|Tutorial de SaProt]] — especialmente la sección de **efecto de mutaciones**, donde el modelo evalúa si una variante pertenece al espacio de proteínas funcionales.