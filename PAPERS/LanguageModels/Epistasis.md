Fenómeno donde el efecto de una mutación depende del contexto genético (otras mutaciones presentes). El efecto no es aditivo.

## Definición matemática

En modelo aditivo simple:
$$fitness(A) = fitness_{wildtype} + \Delta A$$
$$fitness(A, B) = fitness_{wildtype} + \Delta A + \Delta B$$

Pero observamos:
$$fitness(A, B) \neq fitness_{wildtype} + \Delta A + \Delta B$$

La **diferencia** es la epistasis:
$$epistasis = fitness(A,B) - (fitness_{wildtype} + \Delta A + \Delta B)$$

## Tipos

### Epistasis compensatoria
- Mutación A es deletérea sola
- Mutación B compensa a A
- A + B juntas son viables/funcionales

### Epistasis sinérgica
- Dos mutaciones deletéreas por separado
- Juntas son aún peor

### Epistasis magnética
- Efecto de una mutación amplifica el de otra

## Ejemplo

En estructura proteica:
- Posición 100: carga positiva (importante para estructura)
- Posición 150: carga negativa (compensación local)
- Mutación en 100: deletérea
- Mutación en 150: deletérea
- Ambas juntas: viables (mantiene balance electrostático)

## En evolución

Epistasis es común en naturaleza:
- Las proteínas evolucionan no como posiciones independientes
- Sino como sistemas integrados
- Las mutaciones que fijaban eran compensatorias

[[MSA|Alineamientos]] revelan esta co-evolución.

## En métodos clásicos

- **SIFT**: asume no epistasis (independencia de posiciones)
- **PSSM**: asume no epistasis
- **EVMutation**: captura epistasis de segundo orden (pares)
- **DeepSequence**: puede capturar epistasis de orden superior

## En Language Models

El paper argumenta que los language models pueden capturar epistasis compleja porque:
- [[Potts models|Potts models]] apenas hacen orden 2
- Language models tienen capacidad de orden arbitrario
- Entrenar en 250M secuencias permite aprender patrones epistáticos complejos

El scoring mutacional en language models implícitamente modela epistasis.

## En el contexto de proteínas

La existencia de epistasis es la razón por la que:
- Métodos protein-specific funcionan mejor localmente
- Pero foundation models funcionan mejor globalmente
- Porque entienden patrones generales de cómo se estructura la epistasis

## En diseño molecular

En DrugLLM, epistasis también es importante:
- Una modificación química puede afectar múltiples propiedades
- Optimizar LogP podría degradar solubilidad
- [[SAR|SAR]] es esencialmente un problema de epistasis molecular

## [[Fitness landscape|En fitness landscapes]]

Epistasis crea ruggedness del [[Fitness landscape|fitness landscape]]:
- Sin epistasis: landscape sería suave
- Con epistasis: landscape es rugoso, con muchos óptimos locales

Esto hace evolución más compleja y restricta.
