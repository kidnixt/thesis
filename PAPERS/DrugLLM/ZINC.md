Base de datos de moléculas pequeñas sintéticamente accesibles diseñada para virtual screening y molecular docking.

## Características

ZINC contiene:
- ~500 millones de moléculas
- Énfasis en moléculas drug-like (cumplen reglas de Lipinski)
- Información de disponibilidad comercial
- Información de síntesis y costo

## Propósito

ZINC fue diseñado originalmente para:
- **Virtual screening**: buscar moléculas que se unan a proteínas computacionalmente
- **Docking**: moldecular docking de estructuras 3D
- **Lead discovery**: identificar hits potenciales rápidamente

Énfasis en moléculas que pueden ser **sintetizadas y compradas**, no solo teóricamente válidas.

## En Machine Learning

ZINC es ampliamente usado en ML porque:
- Contiene moléculas químicamente viables
- Es de acceso público
- Cubre un espacio molecular representativo de drug-like compounds
- Disponible en múltiples formatos y with 3D coordinates

## En DrugLLM

DrugLLM construye su dataset masivo utilizando:
- **ZINC**: como fuente de moléculas
- **ChEMBL**: como fuente de bioactividades

El process fue:
1. Obtener moléculas de ZINC
2. Filtrar por criterios drug-like
3. Realizar canonicalización química
4. Obtener bioactividades de ChEMBL
5. Generar trayectorias de modificación

Resultado:
- 184.7 millones de moléculas después de filtrado
- 24.6 millones de párrafos de [[NMP|modificación molecular]]
- +10,000 propiedades biológicas y fisicoquímicas

## Ventajas vs ChEMBL

- **ZINC**: focus en síntesis y viabilidad, menos datos de actividad
- **ChEMBL**: focus en bioactividades, menos énfasis en síntesis
- **Combinación**: proporciona cobertura de moléculas viables + bioactividades conocidas

## Clustering

En DrugLLM, las moléculas de ZINC se agrupan mediante:
- Similitud de scaffolds (core estructural)
- RDKit fingerprints
- Dice similarity con threshold 0.60

Esto genera trayectorias coherentes de modificación dentro de familias químicas similares.
