# Masked Language Model (MLM)

## Definición

Un **Masked Language Model** (MLM) es una arquitectura de modelo de lenguaje donde se entrenan redes neuronales para predecir tokens "enmascarados" (ocultos) dentro de una secuencia, dado el contexto de los tokens circundantes.

## Diferencia con modelos autorregresivos

| Característica | MLM (BERT, ESM, SaProt) | Autorregresivo (GPT) |
|----------------|-------------------------|----------------------|
| Dirección | Bidireccional | Izquierda a derecha |
| Entrenamiento | Predice tokens enmascarados | Predice siguiente token |
| Contexto | Ve toda la secuencia | Solo ve tokens anteriores |

## Aplicación en pLMs

Los [[Modelo de lenguaje de proteínas]] como ESM y [[SAPROT]] utilizan MLM porque:

1. Las proteínas tienen dependencias bidireccionales (un residuo afecta a sus vecinos en ambas direcciones)
2. Permite calcular la probabilidad de cualquier residuo dado su contexto estructural
3. Habilita el cálculo de [[Log-Likelihood Ratio|LLR]] para evaluar mutaciones

## Funcionamiento básico

1. Se toma una secuencia: `A-C-D-E-F`
2. Se enmascara un token: `A-C-[MASK]-E-F`
3. El modelo predice una distribución de probabilidad sobre el vocabulario para `[MASK]`
4. Si el modelo predice alta probabilidad para `D`, significa que `D` "encaja" en ese contexto

## En SaProt

SaProt extiende MLM incorporando **tokens estructurales** (3Di/FoldToken), por lo que el modelo no solo ve la secuencia sino también la geometría local:

```
Entrada: (A, token_3Di_1) - (C, token_3Di_2) - [MASK] - (E, token_3Di_4) - (F, token_3Di_5)
```

## Ver también

- [[Log-Likelihood Ratio]]
- [[Embedding de proteínas]]
- [[Zero-shot prediction]]
