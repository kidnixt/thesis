Modelos de grandes capacidades generales, entrenados en datos masivos sin supervisión específica para tarea, que pueden luego ser adaptados a múltiples tareas distintas.

## Características

- **Escala masiva**: entrenados en miles de millones de ejemplos
- **Sin supervisión específica**: aprenden patrones generales sin labels
- **Transferencia**: conocimiento transferible a nuevas tareas
- **Emergencia**: propiedades emergen a cierta escala

## En NLP

Ejemplos canónicos:
- **GPT**: modelos autoregresivos generales
- **BERT**: modelos de masked prediction
- **GPT-3**: primer demostración clara de in-context learning

## En Biología (Innovación del paper)

El paper sobre language models de proteínas **inaugura la idea de foundation models para proteínas**:

> "entrenar un único modelo generalista sobre millones de secuencias y transferir ese conocimiento a proteínas nunca vistas"

Esto contrasta con el paradigma anterior:
- Modelos específicos por familia
- Dependientes de [[MSA|MSAs]] profundas
- No generalizaban a proteínas nuevas

## Trabajos posteriores inspirados

El paper abre toda una línea de foundation models en biología:
- **ESM-1b, ESM-2**: evolución del original
- **MSA Transformer**: incorpora MSAs en el modelo
- **ProtTrans**: enfoque alternativo
- **SaProt**: incorpora estructura
- **ESMFold**: de PLM a predicción de estructura
- **EvoDiff**: generación evolutiva
- **AlphaFold-era PLMs**: híbridos con información estructural

## Ventajas conceptuales

1. **Generalización**: no requiere entrenar por proteína
2. **Escalabilidad**: único modelo para todas las proteínas
3. **Transferencia**: aprende información reutilizable
4. **Económico**: una sola inversión computacional

## Escalabilidad (Scaling laws)

Punto crucial del paper:

> "scaling matters"

Cuando aumentas:
- Cantidad de secuencias
- Tamaño del modelo
- Capacidad Transformer

**Emergen propiedades biológicas nuevas**:
- Predicción de estructura
- Comprensión funcional
- [[Zero-shot prediction|Zero-shot prediction]]

Esto es emergencia, no simplemente "más de lo mismo".

## Relación con [[Zero-shot prediction]]

Foundation models permiten [[Zero-shot prediction|predicción en zero-shot]] porque:
- Aprenden regularidades evolutivas profundas
- Pueden aplicar esas regularidades a proteínas nuevas
- Sin entrenamiento explícito en esa proteína

## Limitaciones actuales

Aunque poderosos, los foundation models actuales:
- Utilizan solo secuencia (la mayoría)
- No incorporan explícitamente estructura 3D (aunque algunos como SaProt lo hacen)
- No entienden contexto celular completo
- Son proxies probabilísticos, no mediciones físicas
