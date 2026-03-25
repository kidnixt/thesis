# Saliency Maps

## Definición

Los **Saliency Maps** (mapas de saliencia) son una técnica de explicabilidad que visualiza qué partes de la entrada son más "importantes" para la predicción del modelo, basándose en el cálculo de gradientes.

## Fundamento matemático

Se calcula el gradiente de la salida (score o predicción) respecto a los embeddings de entrada:

$$\text{Saliency}_i = \left\| \frac{\partial \text{Output}}{\partial \text{Embedding}_i} \right\|$$

## Interpretación

- **Pico alto de saliency**: El modelo es extremadamente sensible a esa posición
- **Saliency bajo**: Esa posición tiene poco impacto en la predicción
- Es como un "indicador de atención": nos dice que los pesos de la red están amplificando la señal de esos tokens específicos

## Ejes en las gráficas

- **Eje X**: Posición del residuo en la secuencia (índice del token)
- **Eje Y**: Magnitud del gradiente (importancia relativa, usualmente normalizada de 0 a 1)

## Aplicación en proteínas

En el contexto de [[Modelo de lenguaje de proteínas|pLMs]] como [[SAPROT]]:

1. Se usa para identificar **residuos críticos** para la [[Estabilidad proteica|estabilidad]]
2. Permite comparar qué regiones influyen en distintas tareas (estabilidad vs termoestabilidad)
3. Ayuda a validar si el modelo "mira" las regiones biológicamente relevantes

## Diferencia entre tareas

Si los Saliency Maps de "Estabilidad" y "Termoestabilidad" no coinciden, sugiere que el modelo ha aprendido representaciones diferentes para estas tareas a pesar de compartir el mismo backbone.

## Limitaciones

- Solo muestra correlación, no causalidad
- Puede ser ruidoso en modelos muy profundos
- Depende de la arquitectura y capa del modelo analizada

## Ver también

- [[SHAP]]
- [[Embedding de proteínas]]
- [[Efecto de mutaciones]]
