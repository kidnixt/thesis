# SHAP (SHapley Additive exPlanations)

## Definición

**SHAP** es un método de explicabilidad basado en la teoría de juegos que asigna un "valor de contribución" (valor de Shapley) a cada característica de entrada para explicar una predicción.

## Fundamento teórico

Los valores de Shapley provienen de la teoría de juegos cooperativos y representan la contribución marginal promedio de cada jugador (en ML, cada feature) al resultado final.

$$\phi_i = \sum_{S \subseteq N \setminus \{i\}} \frac{|S|!(n-|S|-1)!}{n!} [f(S \cup \{i\}) - f(S)]$$

Donde:
- $\phi_i$ es el valor SHAP de la feature $i$
- $S$ son subconjuntos de features sin incluir $i$
- $f$ es la función del modelo

## Aplicación en pLMs

En [[Modelo de lenguaje de proteínas|pLMs]] como [[SAPROT]]:

1. Se analiza qué tokens de entrada "empujan" el score hacia arriba o abajo
2. Se identifican los **Top N tokens** más influyentes
3. En SaProt, el vocabulario incluye aminoácidos Y tokens estructurales (3Di)

## Interpretación visual

- **Color rojo**: Token que empuja el score hacia valores negativos (desfavorable)
- **Color azul**: Token que empuja hacia valores positivos (favorable)
- **Magnitud de la barra**: Fuerza de la contribución

## Cuidados en SaProt

- El vocabulario de SaProt incluye tokens especiales (`<CLS>`, `<SEP>`, `<PAD>`)
- Tokens como "SIM-" podrían ser artefactos del mapeo incorrecto del vocabulario
- Es importante verificar que la herramienta de SHAP mapee correctamente los tokens del modelo

## Ventajas sobre Saliency Maps

| Aspecto | SHAP | [[Saliency Maps]] |
|---------|------|-------------------|
| Base teórica | Teoría de juegos | Gradientes |
| Interpretación | Contribución aditiva | Sensibilidad local |
| Dirección | Muestra si empuja +/- | Solo magnitud |
| Costo computacional | Alto | Bajo |

## Ver también

- [[Saliency Maps]]
- [[Log-Likelihood Ratio]]
- [[Efecto de mutaciones]]
