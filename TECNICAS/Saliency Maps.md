# Saliency Maps

## Definición

Los **Saliency Maps** (mapas de saliencia) son una técnica de explicabilidad que visualiza qué partes de la entrada son más importantes para la predicción de un modelo, calculando gradientes de la salida respecto a la entrada.

## Intuición

Imagina que quieres saber qué partes de una imagen hicieron que un modelo la clasificara como "gato". Los Saliency Maps responden: "si muevo un poquito cada píxel, ¿cuánto cambia la predicción?". Los píxeles donde el cambio es grande son los "importantes".

## Cómo funciona

1. Se tiene un modelo con una entrada $x$ y una salida $y$
2. Se calcula el gradiente: $\frac{\partial y}{\partial x}$
3. La magnitud del gradiente indica la sensibilidad del modelo a cada elemento de la entrada

## Interpretación

- **Valores altos**: El modelo es muy sensible a esa parte de la entrada
- **Valores bajos**: Esa parte tiene poco impacto en la predicción

## Ventajas

- Rápido de calcular (una pasada de backpropagation)
- Aplicable a cualquier modelo diferenciable
- Intuitivo de visualizar

## Limitaciones

- Solo muestra sensibilidad local, no causalidad
- Puede ser ruidoso en redes profundas
- No indica dirección (si empuja hacia + o -)

## Ver también

- [[SHAP]] - Método alternativo de explicabilidad
