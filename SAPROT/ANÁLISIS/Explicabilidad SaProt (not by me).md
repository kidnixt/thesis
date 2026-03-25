
### 1. Cuantificación del Espacio de Salida: El Log-Likelihood Ratio (LLR)

El documento utiliza el [[Score de Mutación SaProt|score de mutación]] como métrica principal. Técnicamente, esto no es una medida de "salud", sino una medida de **sorpresa del modelo**.

- **Fundamento:** SaProt, al ser un modelo de **masked language modeling (MLM)** (similar a BERT/ESM, no autorregresivo), estima una distribución de probabilidad sobre un vocabulario de tokens. El score reportado es un **[[Log-Likelihood Ratio]] (LLR)**.
- **Justificación:** Se realiza este cálculo para medir qué tan desplazada queda la distribución de probabilidad cuando se fuerza un token específico (mutante) en una posición dada, comparado con el token original ([[Wild-type|WT]]).
- **Incoherencia Estadística:** El informe clasifica como "menos favorables" a **D314A (-1.30)** y **S126R (-7.33)**. Desde la teoría de la información, esto es un error de interpretación de magnitudes. Siendo una escala logarítmica, la densidad de probabilidad de S126R es órdenes de magnitud menor. Etiquetarlos bajo la misma categoría ignora la distribución de los datos; -1.30 suele estar dentro del ruido de fondo o de la varianza normal del modelo, mientras que -7.33 es un _outlier_ estadístico claro.


### 2. Filtrado por Clasificación de Cabeza (Task-specific Head)

Se menciona el uso de `Model-Binding_Site_Detection-650M` y el valor "1".

- **Justificación:** El modelo base (backbone) tiene acoplada una **cabeza de clasificación binaria**. El valor "1" es simplemente el resultado de pasar el embedding de esa posición por una función **Sigmoide** con un umbral (threshold) de decisión.
- **Metodología:** El análisis se restringe a los tokens donde el clasificador disparó un "1" (True). Se justifica para reducir la dimensionalidad del análisis y enfocarse en los vectores de alta relevancia para esa tarea específica.

### 3. Alanine Scan: Perturbación de Entrada Sistemática

- **Metodología:** Se reemplaza cada token original por el token representativo de la Alanina.
- **Justificación:** En términos de modelos, esto es una **prueba de robustez ante perturbaciones**. Se busca observar qué posiciones, al ser reemplazadas por un token "neutro" (que tiene una distribución de probabilidad muy plana en el dataset de entrenamiento), generan un colapso en el score de salida. Las "caídas pronunciadas" identifican posiciones con alta **información mutua** respecto a la estabilidad global.

### 4. [[Saliency Maps]]: Atribución Basada en Gradientes

Para explicar qué son los **[[Saliency Maps]]** sin vueltas: es básicamente ver qué tanto se "rompe" o cambia la predicción si mueves un poquito los valores de entrada.

- **Explicación técnica:** Se calcula el gradiente de la salida (el score) respecto a los **embeddings de entrada** (los vectores de 480 dimensiones).
- **Interpretación:** Si una posición tiene un pico de _Saliency_, significa que el modelo es **extremadamente sensible** a esa posición. Es como un "indicador de atención": nos dice que los pesos de la red están amplificando la señal de esos tokens específicos para llegar al resultado.
- **Ejes:** El eje X es la secuencia (el índice del token) y el eje Y es la magnitud de ese gradiente. Picos altos = el modelo está "mirando" ahí para decidir.
    

### 5. Análisis del Espacio Latente ([[Embedding de proteínas|Embeddings]])

El informe menciona que los [[Embedding de proteínas|embeddings]] de 480 dimensiones capturan secuencia y estructura.

- **Justificación:** SaProt no usa tokens de aminoácidos puros, sino **FoldTokens**. Esto significa que el espacio latente está pre-condicionado por un algoritmo de discretización estructural ([[3Di]]).
- **Implicancia:** Los vectores resultantes no viven en un espacio semántico de "letras", sino en un espacio de **formas locales**. Por eso, el modelo puede "predecir" estabilidad sin ejecutar una simulación física; simplemente detecta si el token estructural "encaja" en el contexto de los tokens vecinos. Ver [[Foldseek]] para más detalles.
    

### 6. [[SHAP]]: Descomposición de Contribuciones

- **Metodología:** Se analizan los "Top 15 tokens".
- **Justificación:** [[SHAP]] intenta asignar un "valor de pago" (basado en valores de Shapley) a cada token de entrada.
- **Incoherencia/Duda Técnica:** El informe menciona el token **"SIM-"**. En un pLM, esto no debería existir como aminoácido. Es altamente probable que sea un error en la interpretación de los tokens especiales del modelo (como `<CLS>`, `<SEP>` o `<PAD>`) o un artefacto de la herramienta de visualización (como SHAP for Transformers) que no está mapeando correctamente el vocabulario de SaProt.

---

### Preguntas para tu análisis:

1. **Rango Dinámico:** ¿Por qué no se define un umbral de desviación estándar para los scores? Tratar un -1.30 como significativo sin comparar con la varianza global del modelo en esa proteína es estadísticamente débil.
2. **Discrepancia de Gradientes:** Si los Saliency Maps de "Estabilidad" y "Termoestabilidad" no coinciden, ¿significa que el modelo ha aprendido representaciones disjuntas para estas dos tareas a pesar de compartir el mismo backbone?
3. **Identidad de Tokens:** ¿Qué son exactamente los tokens "verdes" en el SHAP? Si son tokens 3Di, necesitamos el mapeo (ej. ¿es el token 'v' o el 'p'?) para entender qué geometría local está penalizando el modelo.



### 1. El Score de Mutación y la "Aptitud Biológica"

Tienes razón en ser escéptico: el modelo no "sabe" biología en el sentido experimental, sabe **estadística**.

- **Fundamento:** SaProt es un [[Modelo de lenguaje de proteínas|modelo de lenguaje]]. El score que entrega es un **[[Log-Likelihood Ratio]] (LLR)**. Se calcula como $\log(P(\text{mutante}) / P(\text{wild-type}))$.
    
- **Interpretación:** Si el score es negativo, significa que, según los datos evolutivos y estructurales con los que se entrenó el modelo, esa [[Mutación|mutación]] es "poco probable". En la literatura de [[Modelo de lenguaje de proteínas|modelos de lenguaje de proteínas]] (pLMs), se ha demostrado una correlación altísima entre esta "baja probabilidad estadística" y un [[Efecto de mutaciones|efecto deletéreo]] (dañino) en la [[Estabilidad proteica|estabilidad]] o función. No es una verdad absoluta, sino una inferencia basada en que la evolución ya "descartó" esas variantes.
    

### 2. El "Valor = 1" y los Heatmaps

- **Valor = 1:** Se refiere a una **máscara binaria**. El modelo `Model-Binding_Site_Detection-650M` es un clasificador: para cada residuo de la proteína, predice si es un sitio de unión (1) o no (0). Agustina filtró la proteína y se quedó solo con las posiciones donde el modelo marcó un "1" para analizar qué pasa si mutamos específicamente esos puntos clave.
    
- **Heatmaps:** Imagina una cuadrícula. En el eje X están las posiciones de la proteína (ej. 126, 314) y en el eje Y los 20 aminoácidos posibles. El color de cada celda indica el score de mutación.
    
    - **Rojo:** Mutación muy desfavorable (score muy negativo).
        
    - **Azul:** Mutación neutra o favorable (score cercano a 0 o positivo).
        
    - **Propósito:** Ver de un vistazo qué zonas de la proteína son "intocables" (mucho rojo) porque cualquier cambio rompería la estructura o función.
        

### 3. Alanine Scan: ¿Existe y está justificado?

- **¿Existe?:** Sí, es una técnica estándar en bioquímica de laboratorio (wet lab). Se sustituye cada aminoácido por Alanina porque esta tiene una cadena lateral pequeña y neutra que no suele introducir nuevos choques estéricos, pero elimina las interacciones del aminoácido original.
    
- **Justificación:** Hacerlo "in silico" (en la computadora) es una forma rápida de identificar **hotspots**. Si al cambiar un residuo por Alanina el score cae estrepitosamente, significa que ese residuo original era crítico para la estabilidad.
    

### 4. Caídas de score vs. Estabilidad

- **¿Es solo LL?:** En un modelo como ESM-2 (solo secuencia), el score es solo probabilidad de secuencia. Pero **SaProt es "Structure-aware"**.
    
- **El matiz:** SaProt lee "tokens estructurales" (3Di). Por lo tanto, su probabilidad ($P$) está condicionada por la estructura 3D. Si la mutación rompe un puente de hidrógeno o crea un choque en el plegamiento, los tokens estructurales dejarán de "encajar", la probabilidad bajará y el score será muy negativo. Así que sí, en SaProt, el score de mutación es un excelente predictor indirecto de la estabilidad.
    

### 5. Clasificación de Aminoácidos

Agustina usa una clasificación estándar de 5 grupos:

1. **Alifáticos/Hidrofóbicos:** (A, V, I, L, M)
    
2. **Polares sin carga:** (S, T, C, N, Q)
    
3. **Cargados Positivos (Básicos):** (K, R, H)
    
4. **Cargados Negativos (Ácidos):** (D, E)
    
5. **Especiales:** (G, P, W, F, Y - a veces se separan los aromáticos).
    
    Es una forma correcta y aceptada de simplificar el análisis químico.
    

### 6. Escala de -7.33 vs -1.30

Como es una escala logarítmica (base $e$ o base 10), la diferencia es **exponencial**:

- **-1.30 (D314A):** Es una mutación levemente desfavorable. Probablemente la proteína siga funcionando, aunque sea un poco menos estable.
    
- **-7.33 (S126R):** Es un impacto masivo. Un score de -7 sugiere que esa variante es miles de veces menos probable que la original. Es casi seguro que esa mutación desestabiliza totalmente esa región de la proteína.
    

### 7. Embeddings: ¿Secuencia + Estructura?

Exactamente. SaProt utiliza algo llamado **FoldToken**.

- En lugar de ver solo "A-C-D-E", el modelo ve pares: "(A, token_estructural_1) - (C, token_estructural_2)".
    
- El embedding de 480 dimensiones es la representación matemática interna donde el modelo ya mezcló ambas informaciones. No es que las primeras 240 dimensiones sean secuencia y las otras estructura; están "enredadas" (entangled) en el espacio vectorial.
    

### 8. Saliency Maps y Ejes

- **¿Feature importance de embeddings?:** ¡Exacto! Es una técnica de gradiente. Se calcula cuánto cambia la salida del modelo si muevo un poquito los valores del embedding de una posición.
    
- **Pico de Saliency:** Si la posición 126 tiene un pico alto, significa que el modelo "está mirando con mucha atención" esa posición para dar su veredicto de estabilidad.
    
- **Ejes de las gráficas:**
    
    - **Eje X:** Siempre es la posición del residuo en la secuencia (del 1 al final).
        
    - **Eje Y (Score):** Valor del LLR (típicamente de 0 a -10).
        
    - **Eje Y (Saliency):** Valor del gradiente (importancia relativa, suele normalizarse de 0 a 1).
        
    - **Eje Y (Termoestabilidad/Estabilidad):** Valor predicho en grados Celsius o en unidades de energía ($\Delta\Delta G$ predicho).
        

### 9. SHAP y los "Top 15 tokens"

SHAP intenta explicar la predicción "repartiendo la culpa" entre los tokens de entrada.

- Como SaProt tiene un vocabulario de aminoácidos y tokens estructurales (3Di), el análisis SHAP mira cuáles de esos tokens individuales empujaron el score hacia arriba o hacia abajo.
    
- **Top 15 tokens:** Agustina está listando los 15 elementos (ya sean aminoácidos específicos o formas estructurales locales) que más influyeron en que el modelo dijera "esta mutación es mala". Si los tokens "verdes" son exclusivos de la mutación, te están diciendo qué aspecto nuevo (probablemente una estructura local rota) es el responsable del score negativo.
    

**Pregunta para tu bitácora:** Una de las mayores inconsistencias es que el informe trata a D314A (-1.30) como "menos favorable" al igual que a S126R (-7.33), cuando en realidad -1.30 suele estar dentro del rango de tolerancia en muchos pLMs. ¿Se estará sobreestimando el impacto de D314A solo por ser negativo?