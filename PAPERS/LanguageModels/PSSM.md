Position Specific Scoring Matrices. Matriz que contiene las frecuencias (o scores) de cada aminoácido en cada posición de una secuencia, típicamente derivada de un [[MSA|alineamiento múltiple]].

## Estructura

PSSM es una matriz de dimensión N × 20 donde:
- **N**: número de posiciones en la proteína
- **20**: número de aminoácidos estándar
- **Cada entrada**: score del aminoácido i en la posición j

Ejemplo conceptual:
```
Posición 1: A=10, B=2, C=0, ... (aminoácidos comunes, raros, no observados)
Posición 2: A=1, B=15, C=5, ...
...
```

## Cálculo

A partir de [[MSA|MSA]]:
1. En cada posición, contar frecuencia de cada aminoácido
2. Normalizar (frecuencias = countificación)
3. Opcional: aplicar correcciones pseudocount (evitar ceros)

$$PSSM_{i,j} = \log \frac{P(aminoácido_j | posición_i)}{P(aminoácido_j | background)}$$

## Usos

### Scoring de secuencias
Dada una nueva secuencia, calcular qué tan "compatible" es:
$$score = \sum_i PSSM_{i,secuencia_i}$$

Secuencias evolutivamente similares → scores altos.

### Mutation prediction
Mutación $A \to B$ en posición $i$:
$$\Delta score = PSSM_{i,B} - PSSM_{i,A}$$

Si $\Delta score < 0$ → mutación deletérea.

Esto es exactamente lo que hace [[SIFT]].

## En métodos clásicos

- **SIFT**: utiliza PSSM para scoring de mutaciones
- **BLAST**: utiliza PSSM para búsqueda de secuencias
- **HMMs**: extensión probabilística de PSSM

## Limitaciones

- **Independencia**: asume que cada posición es independiente
- **No captura interacciones**: dos mutaciones pueden compensarse, PSSM no lo ve
- **Dependiente de MSA**: calidad depende de alineamiento

## En el paper

El paper demuestra que language models superan métodos basados en PSSM (SIFT) porque pueden capturar:
- Interacciones entre posiciones
- Contexto largo
- Patrones complejos

Sin necesidad de MSA explícito.

## Relación conceptual

- **PSSM**: representación estadística simple de evolución
- **Potts models**: extensión que captura interacciones
- **Language models**: aprendizaje sin restricciones de forma funcional

Es una cadena de complejidad creciente.
