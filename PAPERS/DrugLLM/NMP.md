Paradigma central de entrenamiento utilizado en DrugLLM. El modelo recibe ejemplos de modificaciones moleculares orientadas a una propiedad específica y aprende a inferir cuál sería la siguiente modificación adecuada.

## Idea fundamental

Reformula la optimización molecular como un problema de **predicción secuencial de modificaciones**, en lugar de mapeo directo moléculas → propiedades:

Enfoque clásico:
```
Molécula → Propiedad
```

NMP:
```
Molécula A → Modificación → Molécula B
```

Esto cambia completamente la naturaleza del aprendizaje: el modelo pasa de memorizar estructuras químicas a capturar **reglas implícitas de modificación molecular**.

## Estructura de datos

El paper estructura los datos en **párrafos completos de modificaciones moleculares**:

```
[instrucción, molécula1, molécula2, ..., moléculaN]
```

donde:
- La instrucción describe el objetivo farmacológico (ej: "aumentar solubilidad")
- Cada párrafo contiene ejemplos coherentes asociados a la misma propiedad
- Las moléculas representan una trayectoria de modificación

## Entrenamiento autoregresivo

El modelo utiliza entrenamiento estándar de language modeling:

$$P(x_t | x_1, x_2, ..., x_{t-1})$$

Aprende a generar la siguiente molécula token por token en [[FGT|representación FGT]] utilizando el contexto previo.

## Escalabilidad

El dataset de DrugLLM contiene aproximadamente:
- 184.7 millones de moléculas
- 24.6 millones de párrafos de modificación
- +10,000 propiedades biológicas y fisicoquímicas

Esta enorme diversidad de tareas de modificación es clave para que emerja la capacidad few-shot.

## En el contexto de Few-Shot Learning

[[In-context learning|NMP con in-context learning]] permite que DrugLLM:
- Generalice a propiedades nuevas nunca vistas durante entrenamiento
- Realice optimización con únicamente 8 ejemplos contextuales
- Supere métodos clásicos como JTVAE, VJTNN que colapsan en few-shot (~0.50 success rate vs 0.72 de DrugLLM)

## Diferencia conceptual

- **Paradigma clásico**: entrenar modelo supervisado específico por tarea
- **NMP**: un único modelo aprende trayectorias generales, luego adapta en contexto

Esto conecta directamente con ideas modernas de [[Modelo de lenguaje de proteínas|foundation models]] y reasoning autoregresivo.
