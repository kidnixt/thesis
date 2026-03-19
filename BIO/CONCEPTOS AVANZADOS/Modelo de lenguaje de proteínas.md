Modelo computacional entrenado sobre [[Secuencia de aminoácidos|secuencias]] de [[Proteína]]s para aprender patrones y propiedades biológicas.

## Analogía con lenguaje natural

Así como los modelos de lenguaje (GPT, BERT) aprenden patrones del texto:
- **Texto**: secuencia de palabras
- **Proteína**: secuencia de [[Aminoácido]]s

Los modelos aprenden:
- Qué secuencias "tienen sentido"
- Relaciones entre aminoácidos distantes
- Patrones conservados evolutivamente

## Arquitectura típica

La mayoría usa **Transformers**:
- Procesan secuencias completas
- Capturan dependencias a larga distancia
- Generan representaciones (embeddings) ricas

## Ejemplos de modelos

| Modelo | Características |
|--------|----------------|
| ESM-2 | Solo secuencia, muy grande |
| SaProt | Secuencia + estructura |
| ProtTrans | Familia de modelos basados en T5 |
| AlphaFold | Predicción de estructura (no es PLM típico) |

## Capacidades

Los PLMs pueden:
- [[Anotación funcional]] — clasificar proteínas
- Predecir [[Efecto de mutaciones]] — zero-shot
- Estimar propiedades ([[Estabilidad proteica]], [[Afinidad de unión]], etc.)
- [[Diseño de proteínas]] — generar secuencias nuevas

## SaProt — estructura + secuencia

SaProt es especial porque usa **both** secuencia y estructura:
- Codifica cada residuo con aminoácido + token estructural
- Mejor rendimiento en muchas tareas

Ver [[SAPROT/TUTORIAL|Tutorial de SaProt]] para entender todas las capacidades y tipos de tareas.