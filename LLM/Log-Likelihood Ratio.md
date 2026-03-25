# Log-Likelihood Ratio (LLR)

## Definición

El **Log-Likelihood Ratio** (LLR) es una métrica que mide la diferencia logarítmica entre la probabilidad de una variante (mutante) y la probabilidad del aminoácido original (wild-type) en una posición específica.

## Fórmula

$$LLR = \log\left(\frac{P(\text{mutante})}{P(\text{wild-type})}\right) = \log(P_{mut}) - \log(P_{wt})$$

## Interpretación

| Valor LLR | Probabilidad relativa | Interpretación biológica |
|-----------|----------------------|--------------------------|
| 0 | 100% (igual que WT) | Mutación neutra |
| -1.30 | ~27% del WT | Levemente desfavorable |
| -2.0 | ~13.5% del WT | Desfavorable |
| -7.33 | ~0.06% del WT | Severamente deletérea |
| +1.0 | ~270% del WT | Potencialmente favorable |

## Cálculo de probabilidad relativa

Si el LLR está en base natural (ln):

$$P_{rel} = e^{LLR}$$

**Ejemplos:**
- $e^{-1.30} \approx 0.27$ (27% tan probable como WT)
- $e^{-7.33} \approx 0.0006$ (0.06% tan probable como WT)

## Rango dinámico

Según la literatura (Meier et al., 2021):

- **LLR entre 0 y -2**: Generalmente dentro del "ruido" del modelo; variantes posiblemente neutrales
- **LLR < -4**: Mutaciones con alta probabilidad de ser deletéreas
- **LLR < -7**: Estadísticamente "inexistentes" en el espacio latente del modelo

## Aplicación en SaProt

[[SAPROT]] modifica ligeramente la fórmula para adaptarse a su vocabulario que incluye tokens estructurales (3Di). La probabilidad asignada a cada residuo es la suma de las probabilidades de todos los tokens que contienen ese aminoácido.

## Relación con fitness biológico

Un LLR negativo indica que la mutación es "poco probable" según los datos evolutivos y estructurales del entrenamiento. Se ha demostrado correlación entre LLR negativo y:

- Reducción de [[Estabilidad proteica]]
- Pérdida de [[Función de proteínas|función]]
- [[Efecto de mutaciones|Efectos deletéreos]]

## Ver también

- [[Masked Language Model]]
- [[Mutación]]
- [[Efecto de mutaciones]]
- [[Score LLR]] (análisis específico en SAPROT/ANÁLISIS)
