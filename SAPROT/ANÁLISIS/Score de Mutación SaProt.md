# Score de Mutación SaProt

## Descripción

SaProt predice efectos mutacionales usando el **log odds ratio en la posición mutada**, propuesto originalmente por Meier et al. (2021).

**Interpretación:** Un score positivo significa que la mutación es mejor que el [[Wild-type|wild type]] desde la perspectiva evolutiva (mayor es mejor).

## Fórmula original (Meier et al., 2021)

![[Pasted image 20260325160247.png]]

$$\sum_{t \in T} \left[\log P(x_t = s_t^{mt} \mid x_{\backslash T}) - \log P(x_t = s_t^{wt} \mid x_{\backslash T})\right]$$

Donde:
- $T$ = conjunto de posiciones mutadas
- $s_t^{mt}$ = tipo de residuo del mutante
- $s_t^{wt}$ = tipo de residuo del wild-type
- $x_{\backslash T}$ = contexto (secuencia sin las posiciones mutadas)

## Fórmula adaptada por SaProt

![[Pasted image 20260325160307.png]]

$$\sum_{t \in T} \left[\log \sum_{f \in F} P(x_t = s_t^{mt}f \mid x_{\backslash T}) - \log \sum_{f \in F} P(x_t = s_t^{wt}f \mid x_{\backslash T})\right]$$

Donde:
- $V$ = alfabeto de residuos (20 aminoácidos)
- $F$ = alfabeto [[3Di]] de [[Foldseek]] (tokens estructurales)
- $V \times F$ = producto cartesiano (vocabulario structure-aware)
- $s_t f \in V \times F$ = token structure-aware en el vocabulario de SaProt

**Diferencia clave:** SaProt suma las probabilidades sobre todos los tokens estructurales $f$ que contienen el mismo aminoácido, adaptándose a su vocabulario que combina secuencia y estructura.

## Interpretación práctica

| Score | Significado |
|-------|-------------|
| > 0 | Mutación favorable (mejor que WT) |
| = 0 | Mutación neutra |
| < 0 | Mutación desfavorable (peor que WT) |

## Referencias

- Meier, J., et al. (2021). "Language models enable zero-shot prediction of the effects of mutations on protein function." NeurIPS.
- Su, J., et al. (2024). "SaProt: Protein Language Modeling with Structure-aware Vocabulary."

## Ver también

- [[Log-Likelihood Ratio]] - Concepto general de LLR
- [[Score LLR]] - Análisis de magnitudes
- [[Masked Language Model]] - Arquitectura base
- [[3Di]] - Alfabeto estructural
- [[Foldseek]] - Herramienta de tokenización estructural
- [[Wild-type]] - Secuencia de referencia
