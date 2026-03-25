# LLM - Modelos de Lenguaje

Esta carpeta contiene conceptos fundamentales de Modelos de Lenguaje (Language Models) aplicados a proteínas y bioinformática.

## Conceptos

- [[Masked Language Model]] - Arquitectura base de modelos como ESM y SaProt
- [[Log-Likelihood Ratio]] - Métrica principal para evaluar efecto de mutaciones
- [[Saliency Maps]] - Técnica de explicabilidad basada en gradientes
- [[SHAP]] - Método de atribución basado en valores de Shapley

## Relación con modelos de proteínas

Los [[Modelo de lenguaje de proteínas|modelos de lenguaje de proteínas]] (pLMs) como [[SAPROT]] y ESM utilizan estas técnicas para:

1. **Predicción de mutaciones**: Usando [[Log-Likelihood Ratio|LLR]] para evaluar el efecto de variantes
2. **Explicabilidad**: Usando [[Saliency Maps]] y [[SHAP]] para entender qué residuos son importantes
3. **Embeddings**: Generando representaciones vectoriales ([[Embedding de proteínas|embeddings]]) de secuencias

## Ver también

- [[Embedding de proteínas]]
- [[Zero-shot prediction]]
- [[Efecto de mutaciones]]
