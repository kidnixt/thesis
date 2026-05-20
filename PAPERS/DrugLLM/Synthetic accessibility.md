Métrica que estima cuánto esfuerzo sintético se requiere para sintetizar una molécula. Valores típicamente en rango 1-10, donde valores bajos indican síntesis más fácil.

## Definición

Synthetic Accessibility (SA score) evalúa:
- **Complejidad estructural**: moléculas con motifs raros o altamente complejos
- **Similitud con drogas conocidas**: moléculas similares a drogas comerciales son más fáciles
- **Disponibilidad de precursores**: considerando accesibilidad de building blocks

## Métodos de cálculo

### Descriptores comunes
- Complejidad de fragmentos (BRICS, RECAP)
- Tamaño y rigidez molecular
- Presencia de motifs sintéticamente difíciles

### Machine Learning
- Modelos entrenados en síntesis real
- Predicción basada en características moleculares

## Rango de interpretación

- **SA 1-3**: Síntesis muy fácil (pocas reacciones, precursores disponibles)
- **SA 3-7**: Síntesis moderadamente accesible
- **SA 7-10**: Síntesis muy difícil (muchas reacciones, precursores raros)

## Importancia en Drug Discovery

Synthetic accessibility es crítico porque:
- Una molécula potente pero imposible de sintetizar no es útil
- Afecta costos de desarrollo
- Determina viabilidad de manufacturing

## En DrugLLM

DrugLLM evalúa optimización de SA score:
- Junto con [[LogP|LogP]], [[TPSA|TPSA]], solubilidad
- El modelo debe balancear potencia con viabilidad sintética
- La validación experimental requiere que las moléculas sean sintetizables

En el experimento HCN2, los compuestos generados (HCN2-M1, HCN2-M2) debían ser sintetizables químicamente, lo que fue validado mediante síntesis real.

## Trade-offs

Típicamente existe un trade-off:
- **Moléculas complejas altamente potentes** → difíciles de sintetizar
- **Moléculas simples** → fáciles de sintetizar pero menor potencia

[[Medicinal chemistry|Los medicinal chemists]] deben balancear estos aspectos.

## Limitaciones del SA score

- Es un proxy, no medición real de síntesis
- Puede ser pesimista con motifs nuevos
- Moléculas con síntesis novel podrían ser subestimadas
- No captura todos los aspectos de factibilidad sintética (scalability, reagents, etc.)
