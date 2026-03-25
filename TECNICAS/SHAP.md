# SHAP (SHapley Additive exPlanations)

## Definición

**SHAP** es un método de explicabilidad que asigna a cada característica de entrada un "valor de contribución" basado en los valores de Shapley de la teoría de juegos cooperativos.

## Intuición

Imagina que un grupo de personas (las features) trabajan juntas para producir un resultado (la predicción). SHAP responde: "¿cuánto crédito merece cada persona por el resultado final?". Calcula la contribución promedio de cada feature considerando todas las posibles combinaciones.

## Origen teórico

Los valores de Shapley provienen de la teoría de juegos. Si tienes N jugadores y quieres repartir un premio de forma "justa", el valor de Shapley de cada jugador es su contribución marginal promedio sobre todas las coaliciones posibles.

## Interpretación

- **SHAP positivo**: La feature empuja la predicción hacia arriba
- **SHAP negativo**: La feature empuja la predicción hacia abajo
- **Magnitud**: Fuerza de la contribución

## Propiedades

1. **Eficiencia**: La suma de todos los valores SHAP = predicción - valor base
2. **Simetría**: Features con igual contribución reciben igual valor
3. **Nulidad**: Features que no aportan nada tienen valor 0

## Ventajas

- Base teórica sólida (teoría de juegos)
- Indica dirección (+/-)
- Consistente y aditivo

## Limitaciones

- Computacionalmente costoso (exponencial en el número de features)
- Requiere aproximaciones en la práctica

## Ver también

- [[Saliency Maps]] - Método alternativo basado en gradientes
