Descriptor molecular que suma el área superficial de los átomos polares (principalmente oxígeno y nitrógeno) en una molécula. Medido en unidades Ångström² (Ų).

## Definición

TPSA = suma de superficies de Van der Waals de átomos polares (O, N)

Típicamente rangos observados: 0-300 Ų

## Interpretación

- **TPSA bajo (< 20 Ų)**: molécula muy lipófila, pobre permeabilidad acuosa
- **TPSA moderado (20-130 Ų)**: rango típico para drogas orales
- **TPSA alto (> 130 Ų)**: molécula muy hidrófila, pobre absorción intestinal

## Importancia en ADMET

TPSA predice:
- **Permeabilidad**: capacidad de cruzar membranas
- **Absorción intestinal**: moléculas con TPSA 20-130 tienen mejor absorción
- **Barrera hematoencefálica (BBB)**: valores bajos favorecen penetración
- **Distribución tisular**: afecta dónde se distribuye la droga

## Regla en Drug Discovery

En [[Medicinal chemistry|diseño medicinal]]:
- TPSA < 140 Ų está asociado a mejor permeabilidad intestinal
- Es uno de los predictores más simples de biodisponibilidad

## En DrugLLM

DrugLLM optimiza TPSA como una de las propiedades clave evaluadas:
- Junto con [[LogP|LogP]], solubilidad, [[Synthetic accessibility|synthetic accessibility]]
- Balancear TPSA con lipofilia es crucial: aumentar uno típicamente requiere sacrificar el otro
- El modelo aprende patrones de trade-off entre propiedades

## Ventajas como descriptor

- **Cálculo rápido**: computacionalmente barato
- **Interpretación clara**: relacionado directamente con permeabilidad
- **Generalizable**: funciona para cualquier molécula
- **Establecido**: predictor estándar en drug discovery

## Limitaciones

- Es correlativo, no causal (la polaridad es proxy de múltiples factores)
- No captura información 3D o conformacional
- El efecto exacto depende del contexto biológico específico
