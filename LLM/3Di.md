# 3Di (Alfabeto estructural)

## Definición

**3Di** es un alfabeto de 20 caracteres desarrollado por [[Foldseek]] que representa la geometría local tridimensional de estructuras proteicas. Cada carácter codifica un patrón estructural específico.

## Intuición

Así como las proteínas tienen un alfabeto de 20 [[Aminoácido|aminoácidos]] para la secuencia, 3Di proporciona un alfabeto de 20 "letras estructurales" que describen la forma local alrededor de cada residuo.

## Cómo funciona

1. Para cada residuo, se analiza la geometría de sus vecinos en el espacio 3D
2. Se discretiza esta geometría en una de 20 categorías
3. El resultado es una "secuencia estructural" paralela a la secuencia de aminoácidos

## Ejemplo

```
Secuencia:    M  K  T  A  Y  ...
Token 3Di:    d  d  v  v  p  ...
```

Cada residuo tiene ahora dos representaciones: su aminoácido y su contexto estructural.

## Uso en SaProt

[[SAPROT|SaProt]] combina ambos alfabetos creando un vocabulario de tokens "structure-aware":

- Vocabulario = Aminoácidos × 3Di = 20 × 20 = 400 tokens posibles
- Ejemplo: `Md` representa una Metionina en un contexto estructural tipo "d"

Esto permite que el modelo aprenda patrones que dependen tanto de la secuencia como de la estructura.

## Ventajas

- Comprime información 3D en una representación de secuencia
- Permite usar arquitecturas de modelos de lenguaje sobre estructuras
- Captura contexto local de manera eficiente

## Ver también

- [[Foldseek]] - Herramienta que genera tokens 3Di
- [[SAPROT]] - Modelo que usa 3Di
- [[Score de Mutación SaProt]] - Cómo se usan los tokens 3Di en predicción
