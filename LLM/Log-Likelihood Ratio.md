# Log-Likelihood Ratio (LLR)

## Definición

El **Log-Likelihood Ratio** (LLR) es una métrica estadística que mide la diferencia logarítmica entre dos probabilidades. Se usa para comparar qué tan probable es una observación bajo dos hipótesis diferentes.

## Intuición

Si tienes dos opciones (A y B) y quieres saber cuál es más probable según un modelo, el LLR te dice: "¿cuántas veces más probable es A que B?", expresado en escala logarítmica.

## Fórmula general

$$LLR = \log\left(\frac{P(A)}{P(B)}\right) = \log(P_A) - \log(P_B)$$

## Interpretación

| Valor LLR | Significado |
|-----------|-------------|
| 0 | Ambas opciones igualmente probables |
| > 0 | A es más probable que B |
| < 0 | B es más probable que A |

## Escala logarítmica

El LLR está en escala logarítmica (usualmente base $e$). Para convertir a probabilidad relativa:

$$P_{rel} = e^{LLR}$$

**Ejemplos:**
- LLR = 0 → $e^0 = 1$ (igual probabilidad)
- LLR = -1 → $e^{-1} \approx 0.37$ (A es 37% tan probable como B)
- LLR = -3 → $e^{-3} \approx 0.05$ (A es 5% tan probable como B)

## Ventajas de usar logaritmos

1. Convierte multiplicaciones en sumas (más estable numéricamente)
2. Evita underflow con probabilidades muy pequeñas
3. Interpretación aditiva: LLR(A/C) = LLR(A/B) + LLR(B/C)

## Ver también

- [[Masked Language Model]]
- Aplicación en bioinformática: [[Modelo de lenguaje de proteínas]]
