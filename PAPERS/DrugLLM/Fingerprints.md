Representación vectorial o binaria que captura características estructurales de una molécula de forma compacta y comparable. Los fingerprints permiten calcular similitud molecular rápidamente.

## Tipos de Fingerprints

### Fingerprints topológicos
Basados en la conectividad de la molécula:
- **Morgan fingerprints**: similares a los de Circular fingerprints, utilizan información de vecindario
- **RDKit fingerprints**: implementación de Morgan en la librería RDKit

### Fingerprints farmacóforos
Capturan características químicas relevantes:
- Grupos donadores de hidrógeno
- Aceptadores de hidrógeno
- Grupos hidrofóbicos
- Características aromáticas

### Otras representaciones
- **Bit vectors**: representación binaria (típicamente 1024-2048 bits)
- **Count-based**: guardan conteos en lugar de bits

## Métricas de similitud

Los fingerprints permiten comparar moléculas usando:
- **Tanimoto similarity**: `(A ∩ B) / (A ∪ B)` rango [0, 1]
- **Dice similarity**: similar a Tanimoto pero con diferentes propiedades estadísticas
- **Euclidean distance**: si están en espacio continuo

## RDKit Fingerprints

En DrugLLM específicamente se usan:
- **RDKit fingerprints** para similitud de scaffolds
- **Dice similarity** con threshold 0.60 para clustering molecular

Esto permite agrupar moléculas en **familias químicamente similares** manteniendo coherencia estructural.

## Uso en DrugLLM

Los fingerprints sirven para:

1. **Clustering**: agrupar moléculas similares
   - Moléculas con Dice similarity > 0.60 se agrupan
   - Esto genera "trayectorias coherentes" de modificación

2. **Generación de datos**: construir [[NMP|párrafos de modificación]]
   - Modificaciones dentro de una familia mantienen estructura base
   - Reproduce el comportamiento real de optimización iterativa

3. **Interpretabilidad**: entender qué moléculas son "cercanas"

## Ventajas

- **Rápido**: cálculo muy eficiente de similitud
- **Interpretable**: basados en estructura química real
- **Generalizable**: funcionan para cualquier molécula
- **Establecido**: ampliamente usado en cheminformatics

## Limitación en profundidad

Aunque los fingerprints capturan similitud 2D, no consideran:
- Información 3D/conformacional
- Potencial electrostático
- Dinámica molecular
- Información de solvente
