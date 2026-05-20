# Foldseek

## Definición

**Foldseek** es una herramienta de búsqueda y alineamiento de estructuras proteicas que utiliza el alfabeto [[3Di]] para representar estructuras 3D como secuencias de caracteres.

## Intuición

Foldseek convierte el problema de comparar estructuras 3D (computacionalmente costoso) en un problema de comparar secuencias (mucho más rápido), usando su alfabeto estructural 3Di.

## Funcionamiento

1. **Entrada**: Estructura 3D de una proteína (archivo PDB/CIF)
2. **Proceso**: Analiza la geometría local de cada residuo
3. **Salida**: Secuencia de tokens 3Di que representa la estructura

## Velocidad

Foldseek es órdenes de magnitud más rápido que métodos tradicionales de alineamiento estructural (como TM-align):
- Puede buscar en bases de datos de millones de estructuras en segundos
- Mantiene alta sensibilidad para detectar similitud estructural

## Uso en SaProt

[[SAPROT|SaProt]] usa Foldseek para:
1. Generar los tokens estructurales de entrada
2. Crear el vocabulario combinado (aminoácido + token 3Di)

Sin Foldseek, SaProt no podría incorporar información estructural de manera eficiente.

## Aplicaciones

- Búsqueda de estructuras similares
- Anotación funcional basada en estructura
- Clustering de proteínas por fold
- Generación de tokens para [[Modelo de lenguaje de proteínas|pLMs]]

## Ver también

- [[3Di]] - El alfabeto estructural que genera
- [[SAPROT]] - Modelo que usa tokens de Foldseek
- [[Estructura de proteínas]]
