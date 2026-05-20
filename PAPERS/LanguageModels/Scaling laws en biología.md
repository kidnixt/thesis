Fenómeno observado en machine learning donde aumentar la escala (datos, modelo, compute) produce mejoras en capacidades que a veces son cualitativas, no solo cuantitativas. En biología aplicado a modelos de proteínas.

## Concepto general

En NLP se observó (Kaplan et al., 2020):
- Duplicar datos → ~ 6-8% mejora en pérdida
- Relación power-law: loss ∝ data^(-α)

## En Biología de Proteínas

El paper sobre language models demuestra que scaling laws aplican:

Cuando aumentas:
- **Cantidad de secuencias**: de millones a cientos de millones
- **Tamaño del modelo**: capas, hidden dimension, heads
- **Capacidad Transformer**: parámetros totales

**Emergen propiedades no supervisadas**:
- [[Contact prediction|Predicción de contactos]]
- Comprensión funcional (sin labels de función)
- [[Zero-shot prediction|Predicción en zero-shot]]
- Información estructural implícita

## Resultados del paper

Model scaling muestra:
- Modelos pequeños capturan: estadística local, motifs simples
- Modelos medianos: comienzan a capturar estructura
- Modelos grandes: capturan función, restricciones evolutivas, fitness landscapes

## Emergencia

No es que simplemente "más parámetros = mejor":
- Es que **aparecen capacidades nuevas** cualitativamente distintas
- Un modelo pequeño no puede predecir fitness, por mucho que lo afines
- Un modelo grande con suficientes datos automáticamente obtiene esa capacidad

## Importancia conceptual

Scaling laws sugieren que:
- La información funcional **existe implícitamente en evolución**
- Se necesita suficiente capacidad para extraerla
- Es un fenómeno emergente de escala

## Predicciones

El paper implícitamente predice que aún mayores escalas producirán más emergencia:
- Mejor predicción de estructura
- Mejor entendimiento de función
- Mejor generalización

Esto se confirmó posteriormente con modelos como ESM-2, que escaló aún más.

## En el contexto de foundation models

Scaling laws explican por qué [[Foundation models|foundation models]] funcionan:
- Se entrenan en escala masiva
- Emergen propiedades generales
- Transfieren a nuevas tareas

Sin scaling, no habría emergencia.

## Limitaciones actuales

- No está claro dónde se plateaun: ¿infinito scaling siempre mejora?
- El costo computacional crece exponencialmente
- Algunos problemas pueden no escalear (limitation en los datos mismos)
