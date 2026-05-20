Relación que existe entre la estructura química de una molécula y su actividad biológica o propiedades farmacológicas.

## Concepto fundamental

SAR busca responder: ¿qué modificaciones estructurales afectan la propiedad de interés?

Ejemplos:
- Añadir un grupo methoxy en una posición específica → aumenta afinidad de unión
- Cambiar un átomo de oxígeno por nitrógeno → mejora solubilidad
- Extender una cadena lateral → reduce toxicidad

## En Medicinal Chemistry

SAR es central en [[Medicinal chemistry|química medicinal]] real. Los medicinal chemists utilizan razonamiento empírico sobre SAR para:
- Optimizar moléculas candidatas
- Predecir efectos de cambios estructurales
- Diseñar análogos con mejor perfil farmacológico

## Complejidad

SAR raramente es simple. Frecuentemente es:
- **No-lineal**: el efecto de un cambio depende del contexto
- **Dependiente de contexto**: lo que funciona en una familia de moléculas puede no funcionar en otra
- **Multidimensional**: un cambio puede mejorar una propiedad pero empeorar otra

## En el contexto de DrugLLM

DrugLLM intenta aprender reglas SAR abstractas a partir de pocos ejemplos mediante [[NMP|Next Modification Prediction]].

El paper argumenta que DrugLLM logra inferir SAR generalizable porque:
- Observa millones de trayectorias de modificación durante pretraining
- Aprende patrones comunes de optimización
- Puede aplicar esos patrones en contexto a problemas nuevos

Success rate en optimización biológica de targets ChEMBL desconocidos: ~0.76 (sin entrenamiento supervisado específico).

## Diferencia con métodos clásicos

- **QSAR tradicional**: modelos estadísticos o ML entrenados específicamente por familia
- **SAR conceptual**: razonamiento humano basado en experiencia química
- **SAR aprendido en LLMs**: emergencia de reglas generales a partir de observación masiva de modificaciones

El paradigma de aprender SAR en [[Modelo de lenguaje de proteínas|language models]] es relativamente nuevo y representa un cambio en cómo se entiende la optimización molecular.
