Proceso de razonamiento químico que parte de una molécula objetivo y trabaja hacia atrás para identificar las reacciones químicas y precursores necesarios para sintetizarla.

## Concepto

En síntesis química directa:
```
Precursor A + Precursor B → Molécula objetivo
```

En retrosíntesis:
```
Molécula objetivo ← ruptura retrósintética ← Precursor A + Precursor B
```

## Aplicaciones

Retrosíntesis es crucial para:
- **Planificación sintética**: diseñar rutas de síntesis viables
- **Drug discovery**: asegurar que candidatos propuestos sean sintetizables
- **Manufacturing**: optimizar rutas de síntesis a escala
- **Cost analysis**: evaluar viabilidad económica de síntesis

## Complejidad

El problema es combinatorialmente difícil porque:
- Una molécula puede tener múltiples rutas de síntesis
- Cada ruta tiene diferentes costos, rendimientos, seguridad
- Las reacciones pueden generar byproducts indeseados
- La escalabilidad depende de disponibilidad de precursores

## En AI/ML

Retrosíntesis ha sido un área activa de investigación en ML aplicado a química:
- Métodos basados en templates (reglas químicas)
- Redes neuronales que aprenden patrones de síntesis
- Transformer models para secuencias de transformaciones

## Diferencia crucial con FGT

El paper de DrugLLM enfatiza explícitamente que [[FGT|Functional Group Tokenization]] **NO está diseñado para retrosíntesis**.

Razones:
- FGT optimiza para razonamiento contextual y modificación incremental
- Retrosíntesis requiere decomposición formal de la estructura
- Son objetivos conceptualmente distintos

Aunque FGT usa fragmentos como building blocks, no genera necesariamente rutas sintéticas realizables. DrugLLM genera moléculas, pero la validación experimental requiere síntesis real.

## En validación de DrugLLM

En el experimento con HCN2 inhibitors, los compuestos generados por DrugLLM fueron efectivamente sintetizados mediante síntesis química estándar, demostrando que las moléculas propuestas eran químicamente viables.
