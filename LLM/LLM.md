---
color: var(--mk-color-brown)
---

# 📊 LLM - Modelos de Lenguaje

Conceptos fundamentales de Language Models aplicados a biología molecular y proteínas.

## Temas Principales

### 1. 🏗️ [[Transformer|Transformer — Arquitectura Base]]

Arquitectura transformer: attention, self-attention, bloques, mecanismos core de modelos modernos.

---

### 2. 🎓 [[Masked Language Model|Masked Language Model — Entrenamiento]]

Método de entrenamiento bidireccional: BERT, ESM family, mecanismo de predicción enmascarada.

---

### 3. 📈 [[Log-Likelihood Ratio|Log-Likelihood Ratio — Métrica de Comparación]]

Métrica LLR para comparar probabilidades y efectos en secuencias.

**Conexiones:** [[SAPROT/ANÁLISIS/Score de Mutación SaProt]], [[BIO/MUTACIONES/Efecto de mutaciones]]

---

### 4. 🧬 [[Foldseek|Foldseek — Tokenización Estructural]]

Herramienta que convierte estructuras 3D en secuencias de tokens (3Di).

**Backlinks agregados a:**
- [[3Di]] - Alfabeto estructural resultante
- [[SAPROT/SAPROT]] - Vocabulario structure-aware

---

### 5. 📐 [[3Di|3Di — Alfabeto Estructural]]

Alfabeto de 20 caracteres que representa geometría local de proteínas.

**Conexiones:** Producido por [[Foldseek]], usado en [[SAPROT/SAPROT]]

---

### 6. 💡 [[SHAP|SHAP — Valores de Shapley para Explicabilidad]]

Método de explicabilidad basado en teoría de juegos: valores Shapley.

**Ver también:** [[../TECNICAS/INDEX]]

---

### 7. 🎨 [[Saliency Maps|Saliency Maps — Mapas de Saliencia]]

Atribución por gradientes: visualización de qué posiciones influyen más en predicciones.

**Ver también:** [[../TECNICAS/INDEX]]

---

## Estructura de Conceptos

```
LLM/
├── LLM.md (este índice)
├── INDEX.md (tabla de navegación)
├── Transformer.md
├── Masked Language Model.md
├── Log-Likelihood Ratio.md
├── Foldseek.md
├── 3Di.md
├── SHAP.md
└── Saliency Maps.md
```

---

## Estadísticas

- **Conceptos:** 7 core + técnicas de XAI
- **Conexiones:** Integradas con BIO, SAPROT, PAPERS
- **Aplicaciones:** Proteínas, mutaciones, diseño

---

## Cómo Navegar

1. **Empezar por arquitectura:** [[Transformer]] - la base de todo
2. **Ver índice temático:** [[INDEX]] para tabla categorizada
3. **Explorar aplicaciones:** [[SAPROT/SAPROT]], [[PAPERS/LanguageModels/INDEX]]
4. **Técnicas relacionadas:** [[../TECNICAS/INDEX]] para explicabilidad

**Tip:** LLM + estructura (3Di/Foldseek) = SaProt

