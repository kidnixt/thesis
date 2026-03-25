# Wild-type (WT)

## Definición

El **wild-type** (WT) es la forma "original" o de referencia de una [[Proteína]] o gen, típicamente la variante más común encontrada en la naturaleza o la secuencia de referencia contra la cual se comparan las [[Mutación|mutaciones]].

## Etimología

El término viene de la genética clásica:
- **Wild**: "salvaje", encontrado en poblaciones naturales
- **Type**: tipo o forma

## Uso en análisis de mutaciones

Cuando se estudia el [[Efecto de mutaciones|efecto de una mutación]], siempre se compara contra el WT:

| Notación | Significado |
|----------|-------------|
| D314A | Asp en posición 314 → Ala |
| WT | Secuencia original (Asp en 314) |

## En modelos computacionales

Los [[Modelo de lenguaje de proteínas|pLMs]] como [[SAPROT|SaProt]] calculan scores comparando:
- Probabilidad del aminoácido **mutante**
- Probabilidad del aminoácido **wild-type**

$$\text{Score} = \log P(\text{mutante}) - \log P(\text{WT})$$

Ver [[Score de Mutación SaProt]] para la fórmula completa.

## Consideraciones

- No siempre hay un único WT (pueden existir variantes naturales comunes)
- En contextos clínicos, WT suele referirse a la secuencia de referencia del genoma humano
- En experimentos de laboratorio, WT es la proteína sin modificaciones introducidas

## Ver también

- [[Mutación]]
- [[Variantes proteicas]]
- [[Efecto de mutaciones]]
- [[Log-Likelihood Ratio]]
