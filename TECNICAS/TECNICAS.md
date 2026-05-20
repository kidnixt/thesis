---
color: var(--mk-color-turquoise)
---

# 🔍 TECNICAS - Técnicas de Machine Learning y Explicabilidad

Métodos para entender, interpretar y explicar predicciones de modelos de aprendizaje automático en biología.

## Conceptos Principales

### 1. 🤖 [[XAI|XAI — Explainable Artificial Intelligence]]

Introducción a explicabilidad: por qué es importante, enfoques, aplicaciones en proteínas.

📁 **Relacionado:** [[XAI]]

---

### 2. 🎨 [[Saliency Maps|Saliency Maps — Mapas de Saliencia]]

Técnica de atribución por gradientes: visualizar qué regiones/residuos influyen más en predicciones.

**Aplicación:** Identificar posiciones críticas en proteínas

**Backlinks:**
- [[../LLM/INDEX]] - Técnica general en LLM
- [[../SAPROT/ANÁLISIS/Explicabilidad SaProt]] - Aplicación en SaProt

---

### 3. 📊 [[SHAP|SHAP — Valores de Shapley]]

Explicabilidad basada en teoría de juegos: contribución de cada feature a predicción.

**Aplicación:** Cuantificar importancia de residuos, mutaciones

**Backlinks:**
- [[../LLM/INDEX]] - Método en modelos de lenguaje
- [[../SAPROT/ANÁLISIS/Explicabilidad SaProt]] - Aplicación en SaProt

---

## Estructura

```
TECNICAS/
├── TECNICAS.md (este índice)
├── INDEX.md (tabla de navegación)
├── XAI.md
├── Saliency Maps.md
└── SHAP.md
```

---

## Estadísticas

- **Métodos:** 3 técnicas de explicabilidad
- **Aplicaciones:** Proteínas, mutaciones, modelos de lenguaje
- **Conexiones:** Integradas con LLM, SAPROT, BIO

---

## Cómo Navegar

1. **Empezar por XAI:** [[XAI]] - entender qué es explicabilidad
2. **Explorar métodos:** [[Saliency Maps]], [[SHAP]]
3. **Ver aplicaciones:** [[../SAPROT/ANÁLISIS/INDEX]] para SaProt
4. **Contexto:** [[../LLM/INDEX]] - estos métodos se usan en modelos de lenguaje

**Tip:** Estas técnicas responden: "¿Por qué el modelo predice X?"

