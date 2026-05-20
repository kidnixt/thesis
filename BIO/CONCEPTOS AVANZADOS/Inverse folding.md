Proceso computacional de generar [[Secuencia de aminoácidos|secuencias]] que se plieguen en una [[Estructura de proteínas|estructura]] dada.

## Problema inverso

El problema tradicional en biología de proteínas:
- **Forward**: Secuencia → Estructura (predicción de estructura)
- **Inverse**: Estructura → Secuencia (inverse folding)

## ¿Por qué es útil?

El inverse folding permite:
- Diseñar secuencias para estructuras deseadas
- Explorar el [[Espacio de secuencias proteicas]] compatible con una estructura
- Optimizar secuencias manteniendo la estructura

Complementa las capacidades de [[Zero-shot prediction]] al permitir generar nuevas variantes.

## Aplicaciones

- **[[Diseño de proteínas]]**: crear proteínas con formas específicas
- **Estabilización**: encontrar secuencias más [[Estabilidad proteica|estables]] para una estructura
- **Humanización de anticuerpos**: adaptar secuencias sin perder estructura

## Herramientas

| Herramienta | Tipo |
|-------------|------|
| ProteinMPNN | Red neuronal, muy popular |
| ESM-IF | Basado en ESM |
| SaProt | [[Modelo de lenguaje de proteínas]] con capacidad de diseño |

## En SaProt

SaProt puede realizar inverse folding generando secuencias condicionadas en información estructural, lo que lo diferencia de modelos que solo usan secuencia.

Ver [[SAPROT/TUTORIAL|Tutorial de SaProt]] — sección **Diseño de secuencias (inverse folding)**.