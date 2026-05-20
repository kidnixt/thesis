Sistema de representación molecular que codifica moléculas mediante grupos funcionales y fragmentos estructurales semánticamente relevantes, en lugar de átomos individuales como [[SMILES]].

## Motivación

El problema fundamental que FGT intenta resolver es que [[SMILES|pequeñas modificaciones estructurales en SMILES producen secuencias completamente distintas]]. Esto introduce variabilidad sintáctica que dificulta el [[Modelo de lenguaje de proteínas|aprendizaje contextual]] en LLMs.

FGT reformula el problema: en lugar de trabajar a nivel atómico, trabaja con **unidades semánticas químicamente significativas**.

## Concepto central

FGT representa moléculas mediante:
- Grupos funcionales (methoxy, benzene, carboxylic acid, etc.)
- Motifs químicos más grandes
- Fragmentos que capturan razonamiento químico real

En lugar de:
```
C atomos → C1C2C3... (SMILES)
```

Trabaja con:
```
benzene + methoxy + carboxylic_acid
```

## Características

- **Semánticamente orientado**: las unidades son relevantes químicamente, no solo sintácticamente
- **Reasoning primitives**: los grupos funcionales actúan como unidades básicas de modificación química
- **Reducción de secuencia**: logra ~53% de compresión respecto a SMILES
  - SMILES promedio: 38.22 tokens
  - FGT promedio: 17.86 tokens
- **Cobertura casi total**: ~4800 tokens cubren casi completamente el espacio molecular
- **Más eficiente que alternativas**: supera métodos como RECAP o BRICS

## Diferencia clave con [[Retrosíntesis]]

El paper enfatiza mucho que FGT **NO está diseñado para retrosíntesis ni synthetic planning**. Su objetivo es puramente orientado al razonamiento contextual y modificación molecular incremental.

## Ventajas para LLMs

- **Coherencia contextual**: cambios pequeños en FGT → cambios pequeños en la representación
- **Generalización**: el modelo puede aprender patrones de modificación más robustos
- **Interpretabilidad**: los tokens son químicamente interpretables

## En DrugLLM

FGT es fundamental en DrugLLM porque permite que el modelo:
- Aprenda trayectorias de modificación molecular
- Realice razonamiento contextual sobre cambios químicos
- Modele mejor el reasoning de un medicinal chemist
- Evite hallucinations químicas al trabajar con fragmentos válidos

El paper reporta que la capacidad de [[NMP|Next Modification Prediction]] en few-shot y zero-shot depende críticamente de FGT como representación molecular.
