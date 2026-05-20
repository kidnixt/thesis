# Transformer

## Definición

**Transformer** es una arquitectura de red neuronal basada en mecanismos de atención, introducida en 2017 ("Attention is All You Need"). Es la base de la mayoría de los modelos de lenguaje modernos.

## Componentes principales

1. **Self-Attention**: Permite que cada posición "atienda" a todas las demás posiciones de la secuencia
2. **Multi-Head Attention**: Múltiples cabezas de atención en paralelo
3. **Feed-Forward Networks**: Capas densas después de la atención
4. **Positional Encoding**: Codificación de la posición en la secuencia

## Intuición

A diferencia de las redes recurrentes (RNN/LSTM) que procesan secuencias paso a paso, los Transformers procesan toda la secuencia en paralelo. Cada token puede "ver" directamente a todos los demás tokens.

## Variantes principales

| Tipo | Ejemplo | Uso |
|------|---------|-----|
| Encoder-only | BERT, ESM | Entender secuencias |
| Decoder-only | GPT | Generar texto |
| Encoder-Decoder | T5 | Traducción, resumen |

## En modelos de proteínas

Los [[Modelo de lenguaje de proteínas|pLMs]] usan Transformers porque:
- Capturan dependencias a larga distancia en secuencias
- Generan embeddings contextuales ricos
- Escalan bien con datos y parámetros

Ejemplos:
- **ESM-2**: Transformer encoder-only (similar a BERT)
- **[[SAPROT|SaProt]]**: Transformer con vocabulario structure-aware

## Ver también

- [[Masked Language Model]] - Método de entrenamiento común
- [[Modelo de lenguaje de proteínas]]
- [[Embedding de proteínas]]
