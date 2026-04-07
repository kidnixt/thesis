### **06 de Marzo 2026**

Las estructuras provistas por el laboratorio, al ser analizadas tanto en modelos como en visualizadores, no incluyen los tres primeros elementos de la secuencia (SNN) mencionados previamente. Esto no se debe a un error en los datos, sino a una limitación en la resolución estructural (esto lo agrega ChatGPT como interpretación).

Dado que estos elementos faltantes se encuentran al inicio de la secuencia y no forman parte del núcleo estructural principal (esto también es una interpretación), su ausencia no invalida el análisis general de la estructura ni de las mutaciones estudiadas. 

Por lo tanto, no es necesario descartar las estructuras experimentales ni reemplazarlas completamente por modelos predichos. En cambio, es posible continuar el análisis utilizando las estructuras disponibles, manteniendo consistencia en la numeración de la secuencia (ajustada en −3 posiciones respecto a la secuencia completa).

### **17 de Marzo 2026**

Durante la jornada se plantea como objetivo principal comprender e interpretar correctamente los outputs de los modelos utilizados, en particular SaProt y ESM-3, antes de continuar generando nuevos resultados.

Se realizará una revisión de la documentación y/o literatura asociada a estos modelos para identificar qué representan los valores obtenidos (por ejemplo, si corresponden a likelihood u otro tipo de métrica) y determinar si permiten comparaciones válidas entre variantes (WT vs mutantes).

Adicionalmente, se llevará a cabo una prueba controlada sobre un único caso (WT vs una mutación) con el objetivo de observar el comportamiento de los scores y evaluar si las diferencias relativas pueden ser utilizadas como criterio de análisis.

Como resultado esperado, se busca establecer una interpretación clara de los outputs de los modelos y definir si estos pueden ser utilizados de manera confiable en el análisis comparativo de mutaciones.


### **19 de Marzo 2026**

**Actividad del día:** Sistematización teórica de SaProtHub y organización de recursos.

* **Resumen técnico de SaprotHub:** Se realizó una síntesis completa del tutorial basado en el repositorio oficial ([westlake-repl/SaprotHub](https://github.com/westlake-repl/SaprotHub/blob/main/tutorial.md)). El análisis se centró en definir y diferenciar las capacidades operativas del modelo:  
  * **Análisis Funcional:** Clasificación y regresión a nivel de proteína (categorización y métricas de propiedades).  
  * **Complejos:** Interacción proteína-proteína (tanto en clasificación de existencia como en regresión de afinidad).  
  * **Variantes y Diseño:** Evaluación *zero-shot* para el efecto de mutaciones y técnicas de *inverse folding* para diseño de secuencias a partir de estructuras.  
* **Gestión de información en Obsidian:** Se integró el resumen junto con una biblioteca de enlaces y referencias externas en la base de conocimientos personal, facilitando el acceso centralizado a la documentación del modelo para futuras consultas.

### **24 de Marzo 2026**

Se ha reorganizado el vault de Obsidian para mejorar la trazabilidad de la investigación. Tras la revisión de la documentación oficial de SaProt, se definió un plan de acción orientado a desglosar los fundamentos de los Modelos de Lenguaje (LMs) y las particularidades arquitectónicas de SaProt.

* **Entender qué es realmente un “score”.** El objetivo es profundizar en la interpretación estadística de las salidas del modelo, específicamente en las métricas de [[Log-Likelihood Ratio|Log-Likelihood (LL)]].
  * **Definición** de LL en el contexto de [[Modelo de lenguaje de proteínas|pLMs]] y la interpretación biológica de valores altos vs. bajos.
  * **Variantes de Scoring en [[Mutación|Mutaciones]]:**   
    * Log-Likelihood de una secuencia completa.  
    * Diferencial de LL entre el tipo silvestre (Wild Type) y el mutante   
    * Pseudo-Log-Likelihood (PLL) por posición.  
    * Métricas de tipo energético (Energy-like scores).

* **Representación espacial y [[Embedding de proteínas|embeddings]].**
  * **Generación de embeddings:** Proceso de extracción de vectores de características a partir de la arquitectura del modelo.
  * **Representación de secuencias:** Cómo se integran los *tokens* estructurales en el flujo de datos.
  * **Métricas de Distancia:** Significado biológico y matemático de la proximidad entre proteínas dentro del espacio de [[Embedding de proteínas|embeddings]].   
* **Análisis de Implementación:**  
  * Se analizará el código fuente del [pLM SaProt](https://github.com/westlake-repl/SaProt) para identificar las funciones exactas que calculan el *score* de mutación. En la [wiki](https://github.com/westlake-repl/SaprotHub/wiki/SaprotHub-v2-\(latest\)#introduction-of-saprot-mutation-score) se tiene una información relevante sobre el score. 

“*Saprot predicts mutational effects using the log odds ratio at the mutated position, which was proposed by [Meier et al.](https://proceedings.neurips.cc/paper/2021/hash/f51338d736f95dd42427296047067694-Abstract.html) In the original paper, the calculation is formalized as follows:*”  

![[Pasted image 20260325160247.png]]

“*Saprot slightly modify the formula above to adapt to the structure-aware vocabulary, where the probability assigned to each residue corresponds to the summation of tokens encompassing that specific residue type, as shown below:*”  

![[Pasted image 20260325160307.png]]

### **25 de marzo, 2026**

En la jornada de hoy se intentará hacer un análisis de los dos documentos que fueron provistos por Agustina Serrón: **"Explicabilidad en SaProt"** y **"Exploración y aplicación de SaProt"**.

El objetivo de esta lectura es doble:

1. **Enfoque en XAI (Explicabilidad):** Analizar las técnicas *post-hoc* (como [[SHAP]] y [[Saliency Maps]]) aplicadas al modelo para entender cómo se interpretan las predicciones en sitios de unión y [[Mutación|mutaciones]].
2. **Aplicación Práctica:** Revisar los resultados de los modelos específicos de [[Estabilidad proteica|estabilidad]], termoestabilidad y detección de sitios de unión (*Binding Sites*), con especial atención a los datos de mutagénesis por saturación en sitio único y el cálculo de los *scores* de estabilidad.


### **7 de abril, 2026**

Durante la jornada se plantea como objetivo principal iniciar un análisis directo del código fuente de SaProt, con el fin de comprender cómo se calculan internamente los _scores_ utilizados en la evaluación de secuencias y mutaciones, así como la forma en que el modelo representa dichas secuencias a nivel vectorial.

A diferencia de aproximaciones previas basadas en documentación y tutoriales, el foco se desplaza hacia la implementación concreta del modelo, buscando identificar las funciones responsables del procesamiento de secuencias, la generación de probabilidades y la derivación de métricas utilizadas en tareas de inferencia.

En particular, se intentará localizar en el código:

- Los puntos donde se generan los _logits_ del modelo y su posterior transformación en probabilidades (mediante funciones como _softmax_ o _log-softmax_), ya que estos constituyen la base del cálculo de _scores_.
- Las funciones que implementan la evaluación de secuencias completas o por posición, con el objetivo de determinar si el modelo utiliza esquemas de _masked prediction_ (pseudo-likelihood) o evaluación directa de secuencia.
- La forma en que se calcula el efecto de mutaciones, específicamente si se basa en diferencias de log-probabilidad entre la secuencia _wild type_ y sus variantes mutantes.

De manera complementaria, se abordará el análisis de las representaciones internas del modelo, identificando:

- Cómo se tokenizan las secuencias de aminoácidos antes de ser procesadas.
- Qué estructuras de datos contienen los _embeddings_ generados por el modelo (por ejemplo, _hidden states_ o _last hidden state_).
- Qué dimensiones tienen estas representaciones y cómo se organizan (por residuo o a nivel global de la proteína).

El objetivo de esta sesión no es únicamente ubicar funciones dentro del código, sino establecer una correspondencia clara entre los conceptos teóricos previamente estudiados (como [[Log-Likelihood]] y [[Embedding de proteínas]]) y su implementación concreta en el modelo.

Como resultado esperado, se busca obtener una comprensión operativa de cómo SaProt asigna puntuaciones a secuencias y cómo construye su representación interna de proteínas, sentando una base sólida para análisis posteriores más complejos.