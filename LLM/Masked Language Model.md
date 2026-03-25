# Masked Language Model (MLM)

## Definición

Un **Masked Language Model** (MLM) es una arquitectura de modelo de lenguaje donde se entrenan redes neuronales para predecir tokens "enmascarados" (ocultos) dentro de una secuencia, dado el contexto de los tokens circundantes.

## Diferencia con modelos autorregresivos

| Característica | MLM (BERT) | Autorregresivo (GPT) |
|----------------|------------|----------------------|
| Dirección | Bidireccional | Izquierda a derecha |
| Entrenamiento | Predice tokens enmascarados | Predice siguiente token |
| Contexto | Ve toda la secuencia | Solo ve tokens anteriores |

## Funcionamiento básico

1. Se toma una secuencia: `The cat sat on the mat`
2. Se enmascara un token: `The cat [MASK] on the mat`
3. El modelo predice una distribución de probabilidad sobre el vocabulario para `[MASK]`
4. Si el modelo predice alta probabilidad para `sat`, significa que ese token "encaja" en el contexto

## Intuición

MLM aprende representaciones bidireccionales del lenguaje. A diferencia de GPT que solo "mira hacia atrás", MLM puede usar información de ambos lados para entender el contexto completo.

## Ejemplos de modelos MLM

- BERT (texto)
- RoBERTa (texto)
- ESM (secuencias biológicas)

## Ver también

- [[Log-Likelihood Ratio]]
- Aplicación en bioinformática: [[Modelo de lenguaje de proteínas]]
