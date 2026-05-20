Disciplina que combina química, biología y farmacología para diseñar y optimizar moléculas con propiedades farmacológicas deseables.

## Objetivo

Descubrir y desarrollar nuevas drogas mediante:
- Identificación de targets biológicos relevantes
- Búsqueda de ligandos que modifiquen la función del target
- Optimización de propiedades farmacocinéticas y farmacodinámicas
- Minimización de efectos adversos y toxicidad

## Medicinal Chemist

El medicinal chemist es un químico especializado que:
- Realiza síntesis química de candidatos
- Evalúa relaciones [[SAR|Structure-Activity Relationship]]
- Diseña análogos para mejorar propiedades
- Utiliza intuición química basada en experiencia

El razonamiento de un medicinal chemist típicamente implica:
- Preservar el scaffold (core estructural) central
- Optimizar sustituyentes periféricos
- Balancear múltiples propiedades simultáneamente
- Considerar síntesis y escalabilidad

## En Drug Discovery

Medicinal chemistry es el corazón del pipeline de drug discovery:
- Early stage: identificación y validación de targets
- Lead optimization: mejorar hits iniciales
- Candidate selection: elegir la molécula a llevar a clínica
- Development: asegurar viabilidad farmacocinética y tóxica

## En DrugLLM

El paper enfatiza que el modelo intenta "acercar el razonamiento químico de un medicinal chemist a un Transformer":

- Utiliza [[FGT|Functional Group Tokenization]] que es más cercana al razonamiento humano
- Aprende a preservar scaffolds y modificar periferias ([[SAR|SAR]])
- Realiza optimización incremental similar a como lo haría un chemist
- Las attention maps muestran que presta atención a fragmentos químicamente relevantes

## Optimización multiobjetivo

Un desafío central en medicinal chemistry es la optimización simultánea de múltiples propiedades:
- **Potencia**: afinidad de unión al target
- **Selectividad**: no afectar otros targets
- **ADMET**: absorción, distribución, metabolismo, excreción, toxicidad
- **Síntesis**: que sea químicamente viable sintetizar

DrugLLM todavía tiene limitaciones en optimización multiobjetivo compleja (el paper lo reconoce).

## Validación experimental

La validación experimental en medicinal chemistry es crítica. En DrugLLM, dos compuestos generados (HCN2-M1 y HCN2-M2) fueron sintetizados y testeados experimentalmente, mostrando IC50 ~3x menor que la molécula de referencia (ivabradina).
