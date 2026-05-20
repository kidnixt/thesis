Fraction of sp³ carbons. Descriptor que cuantifica la proporción de átomos de carbono con hibridación sp³ (saturados) respecto al total de carbonos en una molécula.

## Definición

$$FractionCSP3 = \frac{\# carbons\_with\_sp^3\_hybridization}{\# total\_carbons}$$

Rango: 0-1

## Interpretación

- **FractionCSP3 alto (> 0.4)**: molécula más saturada, 3D
- **FractionCSP3 bajo (< 0.2)**: molécula más aromática/planar
- **FractionCSP3 = 0**: totalmente aromática (todos carbons sp²)
- **FractionCSP3 = 1**: totalmente saturada (todos carbons sp³)

## Relevancia en Drug Discovery

### Importancia estructural

Moléculas con mayor FractionCSP3:
- Tienen geometría 3D más diversa
- Pueden explorar más conformaciones
- Típicamente tienen mejor selectividad
- Pueden evitar interacciones no-específicas con aromáticos

### En Medicinal Chemistry

Un trend moderno en drug discovery es aumentar complejidad 3D:
- Moléculas altamente aromáticas tienden a unirse inespecíficamente
- Mayor sp³ permite mayor selectividad
- Propiedades farmacocinéticas pueden mejorar

## En DrugLLM

En zero-shot optimization, la instrucción es:
```
"Increase QED and FractionCSP3"
```

Esto implica:
- Mantener drug-likeness ([[QED|QED]])
- Aumentar diversidad conformacional
- Mejorar selectividad potencial

DrugLLM es evaluado contra LLMs generales que tienen dificultad modificando moléculas para simultáneamente:
- Aumentar FractionCSP3 (añadir carbons saturados)
- Mantener [[QED|QED]] (drug-likeness)

Estos son objetivos en conflicto que requieren razonamiento químico sofisticado.

## Métodos de cálculo

### Directo

Contar átomos sp³ usando RDKit o similar:
```python
from rdkit import Chem
mol = Chem.MolFromSmiles(...)
sp3_count = sum(1 for atom in mol.GetAtoms() if atom.GetHybridization() == Chem.HybridizationType.SP3)
```

### Como descriptor de complejidad

Frecuentemente usado en:
- Complexity scoring
- Molecular generation
- Assessment of scaffold hopping

## Limitaciones

- Solo considera hibridación de carbons, no todo heteroátomos
- No captura verdadera complejidad 3D (conformaciones, rigidez)
- Valores altos no garantizan mejores propiedades farmacocinéticas
