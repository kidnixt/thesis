Modelos estadísticos de máxima entropía que describen la distribución de estados en sistemas con interacciones entre posiciones. En biología, se usan para modelar co-evolución proteica.

## Formulación matemática

Un Potts model para una secuencia de longitud N con alfabeto de q estados (aminoácidos):

$$P(x) = \frac{1}{Z} \exp\left(-E(x)\right)$$

donde la energía es:

$$E(x) = -\sum_i h_i(x_i) - \sum_{i<j} J_{ij}(x_i, x_j)$$

- $h_i$: potencial unario (preferencia individual de posición)
- $J_{ij}$: potencial de pareja (coupling entre posiciones)
- $Z$: función de partición (normalización)

## Interpretación

- **Altas interacciones $J_{ij}$**: dos posiciones co-evolucionan fuertemente
- **Potencial unario negativo**: ese aminoácido es favorecido por la evolución

## En biología molecular

Potts models son útiles para:
- Modelar restrictions evolutivas
- Detectar co-variación (posiciones que se mueven juntas)
- Predecir contact maps (posiciones que interactúan estructuralmente)
- Scoring de mutaciones

## En [[MSA|alineamientos múltiples]]

Se puede "fit" un Potts model a una [[MSA|MSA]] observando frecuencias:
- Frecuencias unarias → $h_i$
- Frecuencias de parejas → $J_{ij}$ (con correcciones por dependencias)

Fitting es una inverse problem: recuperar $h$ y $J$ a partir de frecuencias observadas.

## En [[EVMutation]]

[[EVMutation|EVMutation]] utiliza Potts models para:
1. Fit a cada MSA
2. Usar los parámetros para predecir fitness de mutaciones
3. Capturar interacciones de segundo orden

## Ventajas

- **Fundamentalmente sólido**: máxima entropía da distribución menos sesgada
- **Interpretable**: parámetros tienen significado biológico
- **Principios primeros**: basado en física estadística

## Limitaciones

- **Segundo orden solamente**: modela pares, no órdenes superiores
- **Computacionalmente costoso**: fitting de Potts es NP-hard
- **Dependencia de datos**: requiere muchos datos (MSAs profundas)

## Relación con Language Models

El paper de language models implícitamente **aprende modelos más complejos que Potts**:
- Modelos de orden superior
- Sin restricción de forma funcional
- Aprendidos de datos masivos, no fitted a MSAs específicas

De hecho, un Transformer de 250M secuencias puede aprender relaciones más complejas que lo que captura un Potts model en orden 2.
