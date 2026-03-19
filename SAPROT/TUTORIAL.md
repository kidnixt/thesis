---
banner: https://www.biorxiv.org/content/biorxiv/early/2024/04/19/2023.10.01.560349/F1.large.jpg?width=800&height=600&carousel=1
banner_y: "100"
tags:
  - PLM
  - tutorial
---
**Tutorial based on the SaprotHub repository**

```embed
title: "SaprotHub/tutorial.md at main · westlake-repl/SaprotHub"
image: "https://opengraph.githubassets.com/07454ea73bc5ee01ed636d6224c726782492888c37e09fcada3e22ae4dbcfbd5/westlake-repl/SaprotHub"
description: "Making Protein Language Modeling Accessible to All Biologists - westlake-repl/SaprotHub"
url: "https://github.com/westlake-repl/SaprotHub/blob/main/tutorial.md"
favicon: ""
aspectRatio: "50"
```

## SaProtHub — Tipos de tareas y qué significan realmente

SaProtHub es una plataforma para usar [[Modelo de lenguaje de proteínas]] (basados en SaProt) que permite analizar, evaluar y diseñar [[Proteína]]s sin necesidad de entrenar modelos. Todo se reduce a distintos tipos de tareas que representan formas diferentes de "hacerle preguntas" al modelo.  

En general, estas tareas caen en tres grandes formas de uso: describir proteínas, cuantificar propiedades o explorar cambios y diseño.

---

## 🧠Clasificación a nivel de proteína

Este tipo de tarea toma una [[Proteína]] completa y devuelve una categoría. En esencia, es una forma de **[[Anotación funcional]]** o de describir proteínas automáticamente.

Se usa para responder preguntas como: [[Función de proteínas|qué hace una proteína]], dónde se encuentra en la [[Célula]], a qué [[Familia de proteínas]] pertenece o si tiene ciertas propiedades (como ser [[Solubilidad de proteínas|soluble]], tóxica o antigénica). También puede clasificar aspectos más finos como [[Dominio proteico|dominios]], [[Motivo proteico|motivos]] o tipos de [[Interacción proteína-proteína|interacción]]. 

La idea clave es que el modelo analiza la proteína como un todo y la ubica dentro de categorías aprendidas previamente. Puede ser útil cuando tenés proteínas nuevas o poco caracterizadas y querés una primera interpretación funcional. 

---

## 📊Regresión a nivel de proteína

Acá el modelo no da una categoría sino un número. Ese número representa alguna propiedad continua de la [[Proteína]].

Esto incluye cosas como [[Estabilidad proteica|estabilidad térmica]], [[Afinidad de unión]], [[Actividad enzimática]] o [[Nivel de expresión génica]]. En lugar de decir "qué es", el modelo intenta decir "cuánto vale".

Es importante entender que estos valores son estimaciones del modelo, no mediciones reales. Sirven más para comparar o rankear proteínas que para obtener valores absolutos confiables. 

---

## 🔗Interacción proteína-proteína (clasificación)

En este caso el modelo recibe dos [[Proteína]]s y responde si existe una [[Interacción proteína-proteína]] o cómo interactúan.

Esto se usa para estudiar [[Red de interacción proteica|redes de interacción]], relaciones funcionales entre proteínas o asociaciones con enfermedades. Es una extensión del problema de clasificación, pero ahora enfocada en relaciones en lugar de entidades individuales.

La dificultad acá está en que el modelo tiene que entender no solo cada proteína, sino cómo se combinan.

---

## ⚖️ Interacción proteína-proteína (regresión)

Similar al anterior, pero en lugar de decir si interactúan, el modelo estima **qué tan fuerte es la interacción**.

Esto incluye [[Afinidad de unión]], [[Energía de unión]] o [[Cinética de unión]]. Es útil en contextos como diseño de fármacos o análisis de [[Complejo proteico|complejos proteicos]].

De nuevo, los valores son relativos y sirven principalmente para comparar distintas combinaciones.

---

## 🧬 Zero-shot: efecto de mutaciones

Esta es una de las tareas más importantes y potentes.

El modelo recibe una [[Proteína]] y una o varias [[Mutación|mutaciones]], y devuelve un score que indica el [[Efecto de mutaciones|efecto esperado]] de esos cambios. Este efecto puede estar relacionado con [[Estabilidad proteica]], [[Actividad enzimática]] o [[Fitness biológico]].

La idea clave es que el modelo evalúa si la proteína mutada “tiene sentido” dentro del [[Espacio de proteínas]] que conoce. No es una simulación física ni un experimento, sino una evaluación basada en patrones aprendidos.

Se usa para explorar [[Variantes proteicas]], analizar mutaciones específicas o hacer scanning sistemático. Es especialmente útil en [[Ingeniería de proteínas]].

---

## 🧪 Diseño de secuencias (inverse folding)

Acá el modelo hace lo inverso de lo habitual: en lugar de ir de [[Secuencia de aminoácidos]] a [[Estructura de proteínas]], va de estructura a secuencia.

Le das una estructura y el modelo genera secuencias que podrían plegarse en esa forma (ver [[Plegamiento de proteínas]]). También podés modificar partes específicas y dejar que el modelo complete el resto.

Esto convierte al modelo en una herramienta de diseño, no solo de análisis. Se usa para [[Diseño de proteínas]], optimización funcional o exploración dentro del [[Espacio de secuencias proteicas]].
