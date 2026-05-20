---
color: var(--mk-color-red)
---

# 🤖 SAPROT - Modelo de Lenguaje de Proteínas Structure-aware

**SaProt (Structure-aware Protein language model)** es un modelo foundation que integra información estructural (3Di/Foldseek) además de la secuencia de proteínas.

## Característica Distintiva

A diferencia de modelos como ESM-3 que solo usan secuencia, SaProt introduce un **vocabulario consciente de estructura**: combina tokens de residuos con tokens estructurales derivados de Foldseek (3Di).

### Ventajas

- **Vocabulario structure-aware:** Integración explícita de estructura 3D
- **Rendimiento superior:** Supera baselines en 10+ tareas downstream
- **Escala:** Entrenado en ~40 millones de proteínas + estructuras
- **Versatilidad:** Predicción de mutaciones, function prediction, más

---

## Contenido Documentado

### 📚 [[PAPERS]]
Papers asociados con SaProt:
- SaProt: Protein Language Modeling with Structure-aware Vocabulary
- SaprotHub: Making Protein Modeling Accessible to All Biologists
- Democratizing Protein Language Model Training

### 🎓 [[TUTORIAL]]
Guía práctica de uso: cómo usar SaProt para predicciones en tu investigación.

### 🔗 [[LINKS]]
Enlaces a repositorios, código, modelos pre-entrenados, Google Colab notebooks.

### 🔬 [[ANÁLISIS/ANÁLISIS]]
Análisis técnico y explicabilidad:
- **[[ANÁLISIS/Score de Mutación SaProt]]** - Fórmulas y cálculo del score
- **[[ANÁLISIS/Score LLR]]** - Análisis de Log-Likelihood Ratio
- **[[ANÁLISIS/Explicabilidad SaProt]]** - Técnicas XAI aplicadas

---

## Estructura de Carpetas

```
SAPROT/
├── SAPROT.md (este índice)
├── INDEX.md (tabla de navegación)
├── PAPERS.md (referencias)
├── TUTORIAL.md (guía de uso)
├── LINKS.md (recursos externos)
│
└── ANÁLISIS/
    ├── ANÁLISIS.md (índice de análisis)
    ├── Score de Mutación SaProt.md
    ├── Score LLR.md
    └── Explicabilidad SaProt.md
```

---

## Estadísticas

- **Papers:** 2+ versiones/variantes del modelo
- **Conceptos técnicos:** 3 análisis detallados
- **Recursos:** Links a código, modelos, notebooks Colab

---

## Conexiones con el Vault

- **[[../LLM/INDEX]]** - Arquitectura base (Transformer)
- **[[../LLM/Foldseek]]** + **[[../LLM/3Di]]** - Source de tokens estructurales
- **[[../BIO/CONCEPTOS AVANZADOS/CONCEPTOS AVANZADOS]]** - Embeddings, zero-shot
- **[[../BIO/MUTACIONES/MUTACIONES]]** - Predicción de efectos de mutaciones
- **[[../TECNICAS/INDEX]]** - Explicabilidad aplicada a SaProt

---

## Cómo Navegar

1. **Entiende el modelo:** Este documento + [[INDEX]]
2. **Lee papers:** [[PAPERS]]
3. **Aprende a usar:** [[TUTORIAL]]
4. **Explora análisis:** [[ANÁLISIS/ANÁLISIS]]
5. **Obtén recursos:** [[LINKS]]

**Tip:** SaProt = Sequence (LLM) + Structure (3Di/Foldseek) = estructura-aware language model

