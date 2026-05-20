Método evolutivo clásico para predecir efectos de mutaciones utilizando posiciones scoring matrices derivadas de [[MSA|alineamientos múltiples]].

## Concepto

SIFT utiliza frecuencias independientes de aminoácidos en cada posición:

$$SIFT_{score}(x_i) = P(aminoácido_i | posición, evolución)$$

Si una mutación introduce un aminoácido raro en esa posición → probablemente deletérea.

## Proceso

1. Obtener [[MSA|MSA]] de la proteína
2. En cada posición, calcular frecuencia de cada aminoácido
3. Para nueva mutación: consultar frecuencia del aminoácido mutado
4. Aminoácidos raros → score deletéreo

## Limitaciones

- **Modelado independiente**: asume que cada posición es independiente
- **No captura interacciones**: dos mutaciones pueden interactuar ([[Epistasis|epistasis]])
- **Dependencia de MSA**: requiere alineamientos profundos y específicos por familia
- **Family-specific**: no generaliza entre familias

## En el paper de Language Models

El paper compara el language model contra SIFT como baseline:

- SIFT captura información evolutiva local
- Pero es proteína-específica (requiere entrenar por proteína)
- PLM supera a SIFT sin entrenamiento específico

## Ventajas históricas

- **Simple**: fácil de entender e implementar
- **Rápido**: cálculo muy eficiente
- **Útil**: durante décadas fue el mejor método disponible
- **Interpretable**: resultados claros

## Actual

SIFT sigue siendo usado, pero:
- Es considerado un baseline clásico
- Métodos modernos lo superan consistentemente
- Sigue siendo útil para comparaciones

## Relación con [[Position Specific Scoring Matrices|PSSM]]

SIFT es básicamente un modelo que utiliza PSSM construidas a partir de MSA.
