Método evolutivo que predice efectos de mutaciones utilizando [[Potts models|Potts models]] sobre [[MSA|alineamientos múltiples]] para capturar interacciones de segundo orden.

## Idea central

Mientras que [[SIFT|SIFT]] asume independencia de posiciones, EVMutation modela interacciones:

$$E(x) = \sum_i h_i(x_i) + \sum_{i,j} J_{ij}(x_i, x_j)$$

Donde:
- $h_i$: potencial unario (preferencia individual de posición)
- $J_{ij}$: potencial de pareja (interacción entre posiciones)

## Mejora conceptual

EVMutation reconoce que:
- Ciertas mutaciones pueden compensarse mutuamente
- Posiciones co-evolucionan juntas
- [[Epistasis|La epistasis]] es común

Ejemplo:
- Una mutación en un dominio puede no ser deletérea si hay compensación en otro dominio
- Co-variación en MSA indica acoplamiento evolutivo

## Potts Models

EVMutation utiliza [[Potts models|Potts models]] para estimar $h_i$ y $J_{ij}$ a partir de frecuencias en MSA.

Es matemáticamente más sofisticado que SIFT pero sigue siendo estadístico puro.

## En el paper de Language Models

EVMutation es un baseline importante:
- Captura interacciones (mejor que SIFT)
- Requiere MSAs profundas y proteína-específicas
- PLM supera a EVMutation

El point: incluso métodos sofisticados que modelan interacciones pueden ser superados por un language model generalista.

## Limitaciones

- **Entrenamiento lento**: fitting de Potts models es computacionalmente costoso
- **MSA-dependencia**: requiere alineamientos de calidad
- **Family-specific**: no generaliza
- **Segundo orden solamente**: solo captura pares, no órdenes superiores

## Ventajas

- **Captures co-evolution**: modela interacciones reales
- **Sophisticated**: mejor que métodos basados en frecuencias simples
- **Well-established**: ampliamente usado en la comunidad

## Contexto histórico

EVMutation fue una mejora conceptual importante sobre SIFT, pero ambos comparten la limitación de ser family-specific y requerir MSAs.

El cambio paradigmático del paper es ir a modelos generalistas sin MSAs.
