# DrugLLM — Few-shot Molecular Property Optimization via a Domain-Specialized Large Language Model

## Resumen general

DrugLLM propone una idea bastante distinta a la mayoría de trabajos clásicos de diseño molecular. En lugar de entrenar un modelo para generar moléculas desde cero o predecir propiedades químicas de forma supervisada, el paper reformula el problema de optimización molecular como una tarea autoregresiva de [[DrugLLM/NMP|modificación molecular]]. El modelo aprende secuencias de cambios estructurales entre moléculas y trata de inferir las reglas subyacentes que relacionan [[DrugLLM/SAR|estructura y propiedad]]. Conceptualmente, el paper intenta acercar el razonamiento de un [[DrugLLM/Medicinal chemistry|medicinal chemist]] a un [[LLM/Transformer|Transformer]] entrenado sobre trayectorias de modificaciones.

El objetivo principal es resolver un problema muy importante en drug discovery: cómo optimizar moléculas cuando existen muy pocos ejemplos disponibles. Los métodos tradicionales de machine learning en química suelen requerir decenas de miles de muestras etiquetadas para aprender relaciones [[DrugLLM/SAR|SAR]] complejas. DrugLLM intenta escapar de esa dependencia mediante [[DrugLLM/In-context learning|in-context learning]] y [[BIO/CONCEPTOS AVANZADOS/Zero-shot prediction|few-shot]] reasoning.

---

# Idea principal del paper

La contribución conceptual más importante del trabajo es considerar que la optimización molecular puede modelarse como un proceso secuencial de razonamiento sobre modificaciones químicas. El modelo no aprende simplemente moléculas válidas, sino patrones de cambio estructural asociados a aumentos o disminuciones de propiedades farmacológicas.

La idea central podría resumirse así:

```text
Molécula A → modificación → Molécula B
```

En vez de:

```text
Molécula → propiedad
```

Esto cambia completamente la naturaleza del aprendizaje. El modelo pasa de memorizar estructuras químicas a intentar capturar reglas implícitas de modificación molecular.

---

# Functional Group Tokenization (FGT)

Uno de los aportes más importantes del paper es [[DrugLLM/FGT|FGT (Functional Group Tokenization)]]. El trabajo argumenta que [[DrugLLM/SMILES|SMILES]] no es una representación adecuada para LLMs porque pequeñas modificaciones estructurales pueden producir secuencias completamente distintas. Esto introduce una enorme variabilidad sintáctica que dificulta el aprendizaje contextual.

[[DrugLLM/FGT|FGT]] intenta solucionar esto representando moléculas mediante grupos funcionales y fragmentos estructurales semánticamente relevantes. En lugar de trabajar a nivel atómico como [[DrugLLM/SMILES|SMILES]], el modelo trabaja con motifs químicos más cercanos al razonamiento humano en [[DrugLLM/Medicinal chemistry|química medicinal]].

El paper enfatiza mucho que [[DrugLLM/FGT|FGT]] no está diseñado para [[DrugLLM/Retrosíntesis|retrosíntesis]] ni para synthetic planning. Su objetivo es servir como una representación orientada al razonamiento contextual. Los grupos funcionales son tratados como “reasoning primitives”, es decir, unidades semánticas básicas de modificación química.

[[DrugLLM/FGT|FGT]] también reduce significativamente la longitud de secuencia. El paper reporta:

```text
SMILES promedio: 38.22 tokens
FGT promedio: 17.86 tokens
```

lo que representa aproximadamente un 53.27% de compresión.

Además, el vocabulario resultante es mucho más eficiente que métodos como RECAP o BRICS. [[DrugLLM/FGT|FGT]] logra casi cobertura total del espacio molecular usando apenas ~4800 tokens.

---

# Paradigma NMP (Next Modification Prediction)

El paradigma central del entrenamiento es llamado [[DrugLLM/NMP|Next Modification Prediction (NMP)]]. El modelo recibe ejemplos de modificaciones moleculares orientadas a una propiedad específica y debe inferir cuál sería la siguiente modificación adecuada.

El paper estructura los datos como párrafos completos de modificaciones moleculares. Cada párrafo contiene ejemplos coherentes asociados a una misma propiedad o tendencia farmacológica. Por ejemplo, un párrafo puede contener múltiples modificaciones asociadas a aumentar solubilidad o disminuir [[DrugLLM/IC50|IC50]].

La entrada general tiene la forma:

```text
[instrucción, molécula1, molécula2, ..., moléculaN]
```

donde la instrucción describe el objetivo farmacológico.

El modelo utiliza entrenamiento autoregresivo estándar:

$$P(x_t | x_1, x_2, ..., x_{t-1})$$

y aprende a generar la siguiente molécula token por token utilizando el contexto previo.

---

# Dataset y escala de entrenamiento

El paper construye un dataset extremadamente grande utilizando [[DrugLLM/ZINC|ZINC]] y [[DrugLLM/ChEMBL|ChEMBL]]. Después de filtrar moléculas drug-like y realizar canonicalización química, los autores generan aproximadamente:

- 184.7 millones de moléculas
- 24.6 millones de párrafos de [[DrugLLM/NMP|modificación]]
- más de 10.000 propiedades biológicas y fisicoquímicas

Esto es importante porque el trabajo sugiere que la capacidad [[BIO/CONCEPTOS AVANZADOS/Zero-shot prediction|few-shot]] emerge cuando el modelo observa una enorme diversidad de tareas de modificación molecular durante pretraining.

El clustering molecular se realiza mediante similitud de scaffolds utilizando [[DrugLLM/Fingerprints|fingerprints RDKit]] y Dice similarity con threshold 0.60.

---

# Arquitectura del modelo

DrugLLM utiliza un Transformer decoder relativamente estándar. El modelo posee:

- 32 capas
- 32 attention heads
- hidden dimension de 4096
- aproximadamente 7B parámetros

El entrenamiento utiliza AdamW, cosine annealing, fp16 y ZeRO stage 3.

Lo realmente novedoso no es tanto la arquitectura, sino la formulación del problema y la representación molecular.

---

# Few-shot molecular optimization

La evaluación principal consiste en darle al modelo unos pocos ejemplos de modificaciones junto con una molécula objetivo y pedirle que genere una nueva molécula optimizada.

Las propiedades fisicoquímicas evaluadas incluyen:

- [[DrugLLM/LogP|LogP]]
- solubilidad
- [[DrugLLM/TPSA|TPSA]]
- [[DrugLLM/Synthetic accessibility|synthetic accessibility]]

Los resultados muestran algo bastante importante: modelos clásicos como JTVAE, VJTNN y MoLeR prácticamente colapsan a comportamiento aleatorio en este escenario [[BIO/CONCEPTOS AVANZADOS/Zero-shot prediction|few-shot]]. Sus success rates rondan ~0.50.

DrugLLM, en cambio, mejora progresivamente con más contexto y alcanza aproximadamente 0.72 de success rate.

El paper enfatiza mucho que logra performance comparable a GNNs entrenadas con ~34k moléculas usando únicamente 8 ejemplos contextuales.

Ese es probablemente uno de los claims más fuertes del trabajo.

---

# Optimización de actividades biológicas

El paper también evalúa actividades biológicas mucho más complejas utilizando targets ChEMBL no vistos durante entrenamiento. Como no es viable validar miles de moléculas experimentalmente, utilizan ChemProp como predictor de propiedades biológicas.

Aquí aparece una limitación importante del trabajo: gran parte de los benchmarks biológicos dependen de modelos predictivos auxiliares y no de wet-lab real.

Aun así, DrugLLM supera consistentemente a los baselines clásicos y alcanza success rates de hasta 0.76 en algunos targets Ki/IC50.

El paper interpreta esto como evidencia de que el modelo logra inferir reglas SAR abstractas a partir de pocos ejemplos.

---

# Zero-shot molecular optimization

Otra sección importante es [[BIO/CONCEPTOS AVANZADOS/Zero-shot prediction|zero-shot]] optimization. Aquí el modelo recibe únicamente instrucciones en lenguaje natural como:

```text
Increase [[DrugLLM/QED|QED]] and [[DrugLLM/FractionCSP3|FractionCSP3]]
```

sin ejemplos explícitos.

DrugLLM es comparado contra:

- GPT-4
- ChatGPT3.5
- ChatGLM
- Meditron
- BioMedLM

El resultado importante es que los LLMs generales entienden parcialmente las instrucciones, pero tienen dificultades para producir modificaciones moleculares útiles. DrugLLM supera ampliamente a todos los modelos evaluados.

Esto sugiere que el conocimiento químico especializado y la representación [[DrugLLM/FGT|FGT]] son mucho más importantes que simplemente aumentar escala del modelo.

---

# Aplicación real: HCN2 inhibitors

La parte más fuerte del paper es probablemente la validación experimental.

Los autores utilizan ivabradina como molécula inicial y aplican DrugLLM para generar nuevos inhibidores HCN2. El modelo recibe tres pares de ejemplos de optimización y produce nuevas moléculas candidatas.

Dos compuestos generados, HCN2-M1 y HCN2-M2, fueron sintetizados y testeados experimentalmente mediante [[DrugLLM/Patch-clamp|patch-clamp]] en células HEK293.

Ambos mostraron IC50 aproximadamente tres veces menor que ivabradina.

Esto es extremadamente importante porque muchos papers de molecular generation nunca validan experimentalmente sus moléculas.

También analizan attention maps y observan que el modelo presta atención a regiones químicamente relevantes como methoxy groups y el benzazepine moiety, conocidos por su importancia en interacciones HCN2.

---

# Aspectos conceptuales importantes

El modelo muestra una tendencia emergente a preservar el scaffold central de las moléculas mientras modifica regiones periféricas. Esto no fue impuesto explícitamente, sino que emerge del entrenamiento y de la estructura [[DrugLLM/FGT|FGT]].

Esto es muy interesante porque reproduce comportamientos típicos de [[DrugLLM/Medicinal chemistry|medicinal chemistry]] real, donde normalmente se preserva el core estructural y se optimizan sustituyentes periféricos.

El paper argumenta que [[DrugLLM/FGT|FGT]] ayuda además a reducir hallucinations químicas porque trabaja directamente con fragmentos funcionales válidos y utiliza constraints semánticos implícitos.

---

# Limitaciones del trabajo

El paper reconoce varias limitaciones importantes. La primera es que zero-shot optimization todavía es relativamente simple. DrugLLM no incorpora información estructural de proteínas, docking ni geometría 3D explícita.

Tampoco maneja bien optimización multiobjetivo compleja. Las evaluaciones generalmente involucran una o dos propiedades simultáneas, pero problemas reales de ADMET requieren optimización multidimensional mucho más difícil.

Otra limitación importante es que la validación wet-lab sigue siendo pequeña. Aunque los resultados sobre HCN2 son interesantes, dos moléculas no son suficientes para demostrar robustez farmacológica general.

Además, gran parte del benchmark biológico depende de predictors neuronales auxiliares, lo que introduce riesgo de bias o sobreestimación del rendimiento real.

---

# Interpretación general

DrugLLM es importante porque cambia el framing conceptual del problema. El paper no trata simplemente de generar moléculas válidas, sino de aprender trayectorias de [[DrugLLM/NMP|modificación molecular]] mediante razonamiento contextual.

Ese cambio conceptual acerca el problema de molecular optimization a ideas modernas de [[LanguageModels/Foundation models|foundation models]], [[DrugLLM/In-context learning|in-context learning]] y reasoning autoregresivo.

La verdadera innovación probablemente no sea el [[LLM/Transformer|Transformer]] en sí, sino la idea de representar química como secuencias de modificaciones estructurales semánticamente interpretables.

El trabajo sugiere que los futuros modelos de drug discovery podrían parecerse menos a modelos supervisados clásicos y más a sistemas capaces de razonar contextualmente sobre relaciones [[DrugLLM/SAR|SAR]] utilizando conocimiento aprendido durante pretraining masivo.