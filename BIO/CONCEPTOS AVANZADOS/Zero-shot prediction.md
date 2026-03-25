Capacidad de un modelo para hacer predicciones sobre datos nuevos sin haber sido entrenado específicamente para esa tarea.

## En el contexto de proteínas

Un [[Modelo de lenguaje de proteínas]] con capacidad zero-shot puede:
- Predecir [[Efecto de mutaciones]] sin datos experimentales de esa proteína
- Evaluar [[Variantes proteicas]] sin entrenamiento supervisado
- Estimar propiedades generalizando desde datos de entrenamiento

## ¿Cómo funciona?

El modelo no predice directamente un valor, sino que evalúa:
- Qué tan "natural" o "plausible" es una secuencia
- La probabilidad relativa de variantes (usando [[Log-Likelihood Ratio|LLR]])
- Si la secuencia pertenece al [[Espacio de proteínas]] aprendido

## Ventajas

- **Sin datos experimentales**: no requiere datos específicos de la proteína de interés
- **Escalable**: puede evaluar millones de variantes rápidamente
- **General**: funciona para cualquier proteína

## Limitaciones

- Menos preciso que modelos supervisados específicos
- No captura efectos muy específicos del contexto
- Requiere calibración para valores absolutos

## En SaProt

SaProt tiene excelentes capacidades zero-shot para predecir el efecto de [[Mutación|mutaciones]] sobre [[Fitness biológico]], [[Estabilidad proteica]] y otras propiedades. El [[Score de Mutación SaProt]] es la métrica utilizada para cuantificar estas predicciones.

Ver [[SAPROT/TUTORIAL|Tutorial de SaProt]] — la sección **Zero-shot: efecto de mutaciones** es una de las aplicaciones más potentes del modelo.