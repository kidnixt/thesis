Quantitative Estimation of Drug-likeness. Métrica que cuantifica cómo de "parecida" es una molécula a una droga conocida, considerando múltiples características fisicoquímicas simultáneamente.

## Características consideradas

QED combina:
- [[LogP|Lipofilia (LogP)]]
- Peso molecular
- [[TPSA|Polaridad (TPSA)]]
- Donadores de hidrógeno
- Aceptadores de hidrógeno
- Densidad rotacional (rotatable bonds)
- Aromaricidad

## Rango

- Escala 0-1
- **QED > 0.6**: buena drug-likeness
- **QED < 0.4**: características menos favorables para droga

## Metodología

QED utiliza distribuciones desconocidas de drogas comerciales como referencia:
- Calcula cuándo propiedades de una molécula match con drogas conocidas
- Penaliza desviaciones del rango típico de drogas

## En Drug Discovery

QED es útil para:
- **Early filtering**: eliminar moléculas poco drug-like
- **Prioritization**: jerarquizar candidatos
- **Balancing**: asegurar que optimizaciones no sacrifiquen drug-likeness
- **Generative models**: como score para control de calidad

## En DrugLLM

En el benchmark de zero-shot optimization, DrugLLM recibe instrucciones como:
```
"Increase QED and FractionCSP3"
```

Comparado contra:
- GPT-4
- ChatGPT 3.5
- BioMedLM
- Otros LLMs generales

DrugLLM supera ampliamente porque:
- Tiene conocimiento especializado de química
- [[FGT|La representación FGT]] facilita razonamiento químico
- Fue preentrenado en trayectorias de modificación molecular

## Ventajas

- **Integral**: considera múltiples propiedades a la vez
- **Establecido**: métrica reconocida en drug discovery
- **Fácil de calcular**: implementado en librería RDKit
- **Interpretable**: refleja intuición de drug-likeness

## Limitaciones

- Es un agregado de propiedades, cada una con sus limitaciones
- Puede penalizar moléculas novel con propiedades útiles
- No captura toda la complejidad de drug-likeness real
