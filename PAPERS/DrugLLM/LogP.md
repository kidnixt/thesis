Descriptor molecular que cuantifica la hidrofobicidad/lipofilia de una molécula. LogP es el logaritmo del coeficiente de partición entre octanol y agua.

## Definición matemática

$$\log P = \log \frac{[solute]_{octanol}}{[solute]_{water}}$$

## Interpretación

- **LogP > 0**: molécula es lipófila (prefiere fase orgánica)
- **LogP < 0**: molécula es hidrófila (prefiere fase acuosa)
- **LogP ~ 0**: molécula es aproximadamente neutral

## Importancia en Drug Discovery

LogP es crítico porque afecta:
- **Absorción**: penetración intestinal, permeabilidad
- **Distribución**: cómo se distribuye entre tejidos
- **Metabolismo**: accesibilidad a enzimas metabolizadoras
- **Excreción**: si se reabsorbe o excreta

## Reglas de Lipinski

LogP < 5 es uno de los criterios en las famosas reglas de Lipinski para drug-likeness:
- Peso molecular < 500 Da
- LogP < 5
- Donadores de H < 5
- Aceptadores de H < 10

## En DrugLLM

DrugLLM evalúa optimización de LogP como una de las propiedades fisicoquímicas clave:
- Junto con [[TPSA|TPSA]], solubilidad, [[Synthetic accessibility|synthetic accessibility]]
- El modelo aprende a modificar moléculas para aumentar/disminuir LogP
- Balancear LogP con otras propiedades es un aspecto de optimización multiobjetivo

## Métodos de cálculo

- **Predicción**: algoritmos como AlogP, MLogP basados en contribuciones de átomos
- **Experimental**: medición mediante partición octanol-agua real
- **SMILES-basado**: descriptores derivados de [[SMILES|representación SMILES]]

## Limitaciones

- Es un predictor, no medición directa (varía según método)
- Algunas moléculas pueden tener comportamiento anómalo
- No captura todos los aspectos de lipofilia (polaridad, etc.)
