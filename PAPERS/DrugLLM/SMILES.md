Notación lineal que representa la estructura molecular de moléculas orgánicas. SMILES es el acrónimo de Simplified Molecular Input Line Entry System.

## Características principales

SMILES codifica moléculas como cadenas de texto mediante reglas específicas:
- Átomos se representan con sus símbolos químicos (C, N, O, etc.)
- Enlaces simples se omiten (están implícitos)
- Enlaces dobles se representan con `=`
- Enlaces triples con `#`
- Anillos con dígitos que cierran la cadena

Ejemplo:
```
Benceno: c1ccccc1
Etanol: CCO
```

## Ventajas

- **Compacto**: representación lineal fácil de procesar
- **Estándar**: ampliamente usado en cheminformatics
- **Químicamente válido**: contiene información de estructura molecular
- **Computacionalmente eficiente**: bajo costo de parsing

## Limitaciones en Machine Learning

Sin embargo, SMILES presenta un problema importante para LLMs:

- **Invarianza ambigua**: la misma molécula puede tener múltiples representaciones SMILES válidas
- **Variabilidad sintáctica**: pequeños cambios estructurales pueden producir secuencias completamente distintas
- **Difícil para aprendizaje contextual**: dificulta que LLMs aprendan patrones semánticos químicos

## En DrugLLM

DrugLLM reemplaza SMILES con [[FGT|Functional Group Tokenization]] precisamente para evitar estos problemas de variabilidad sintáctica.

El paper muestra que SMILES promedia 38.22 tokens por molécula, mientras que FGT logra 17.86 tokens (~53% compresión).

## Relación con otros formatos

Existen alternativas como:
- **InChI**: más canónica pero más verbosa
- **Motifs químicos**: más semánticos pero menos generales
- **3D structures**: contienen información geométrica pero requieren cálculo adicional
