Capacidad de un modelo de aprender de ejemplos proporcionados en el prompt sin actualizar sus pesos. El modelo adapta su comportamiento basándose únicamente en el contexto inmediato.

## Diferencia con Fine-tuning

- **Fine-tuning**: actualiza pesos del modelo para adaptarse a una tarea
- **In-context learning**: no actualiza pesos, solo utiliza ejemplos en el prompt como guía

## Mecanismo

En [[Transformer|Transformers]], el in-context learning ocurre a través del [[Embedding de proteínas|attention mechanism]]:
- El modelo lee ejemplos proporcionados
- Construye representaciones que capturan el patrón
- Aplica ese patrón a nuevas entradas

Matemáticamente, el modelo utiliza el contexto para condicionar su predicción:
$$P(y | x, ejemplos) \neq P(y | x)$$

## Variantes

### Few-shot learning
Se proporcionan pocos ejemplos (típicamente 2-8):
```
Ejemplo 1: input1 → output1
Ejemplo 2: input2 → output2
Tarea: input3 → ?
```

### Zero-shot
Se proporciona únicamente una instrucción en lenguaje natural sin ejemplos.

## En DrugLLM

DrugLLM utiliza in-context learning mediante [[NMP|Next Modification Prediction]]:

1. **Few-shot molecular optimization**
   - Se proporcionan 8 pares de moléculas modificadas
   - El modelo generaliza la regla de optimización
   - Genera nuevas moléculas optimizadas para la misma propiedad

2. **Success rate comparativo**
   - Modelos clásicos (JTVAE, VJTNN): ~0.50 (colapsan en few-shot)
   - DrugLLM: ~0.72 (mejora con más contexto)

3. **Comparación con supervivientes generales**
   - GPT-4, ChatGPT 3.5, etc. entienden instrucciones en lenguaje natural
   - Pero no pueden generar modificaciones químicas útiles
   - DrugLLM supera ampliamente porque tiene [[FGT|representación especializada]]

## Emergencia en Scaling

El paper sugiere que in-context learning emerge cuando:
- El modelo observa enorme diversidad de tareas durante pretraining
- Se entrena en escala masiva
- Puede generalizar a tareas composicionales nuevas

Esta es una característica central de [[Modelo de lenguaje de proteínas|foundation models]].

## Limitaciones

- Funciona mejor con ejemplos similares a tareas durante pretraining
- Puede ser sensible al orden de ejemplos
- No reemplaza fine-tuning para tareas muy especializadas
