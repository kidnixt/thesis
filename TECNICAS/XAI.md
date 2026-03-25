# XAI (Explainable AI)

## Definición

**XAI** (Explainable Artificial Intelligence) es el campo que busca hacer que las decisiones de modelos de machine learning sean interpretables y comprensibles para humanos.

## ¿Por qué es importante?

Los modelos de deep learning son "cajas negras": dan predicciones pero no explican por qué. XAI busca responder:
- ¿Qué partes de la entrada influyeron en la predicción?
- ¿El modelo está usando características relevantes?
- ¿Podemos confiar en esta predicción?

## Categorías de métodos

### Post-hoc (después del entrenamiento)
Explican modelos ya entrenados sin modificarlos:
- [[Saliency Maps]] - Basado en gradientes
- [[SHAP]] - Basado en valores de Shapley
- LIME - Aproximaciones locales lineales

### Intrínsecos
Modelos diseñados para ser interpretables:
- Modelos lineales
- Árboles de decisión
- Mecanismos de atención visualizables

## Aplicación en proteínas

En [[Modelo de lenguaje de proteínas|pLMs]] como [[SAPROT|SaProt]], XAI permite:
- Identificar qué residuos influyen en una predicción de [[Estabilidad proteica|estabilidad]]
- Visualizar qué regiones son críticas para un [[Score de Mutación SaProt|score de mutación]]
- Validar que el modelo "mira" regiones biológicamente relevantes

## Técnicas principales

| Técnica | Base | Qué muestra |
|---------|------|-------------|
| [[Saliency Maps]] | Gradientes | Sensibilidad del modelo |
| [[SHAP]] | Teoría de juegos | Contribución de cada feature |
| Attention Maps | Arquitectura | Qué tokens atienden a cuáles |

## Ver también

- [[Saliency Maps]]
- [[SHAP]]
