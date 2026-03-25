# Tesis de Maestría en Investigación

Repositorio de documentación y recursos para tesis de maestría en investigación.

## Estructura de Directorios

```
thesis/
├── BIO/                    # Fundamentos de biología molecular y proteínas
│   ├── CONCEPTOS AVANZADOS/   # Temas avanzados (pLMs, embeddings, zero-shot)
│   ├── CONTEXTO CELULAR/      # Proteínas en el contexto celular
│   ├── DISEÑO/                # Diseño de proteínas
│   ├── FUNCIÓN/               # Función de proteínas
│   ├── FUNDAMENTOS/           # Conceptos básicos de biología molecular
│   ├── INTERACCIONES/         # Interacciones proteína-proteína
│   ├── MUTACIONES/            # Efectos de mutaciones, wild-type, fitness
│   └── PROPIEDADES/           # Propiedades físico-químicas de proteínas
│
├── LLM/                    # Conceptos de Modelos de Lenguaje
│   ├── Transformer.md         # Arquitectura base
│   ├── Masked Language Model.md # MLM (BERT, ESM)
│   ├── Log-Likelihood Ratio.md  # Métrica LLR
│   ├── Foldseek.md            # Herramienta de tokenización estructural
│   └── 3Di.md                 # Alfabeto estructural
│
├── TECNICAS/               # Técnicas de ML y Explicabilidad
│   ├── XAI.md                 # Introducción a Explainable AI
│   ├── Saliency Maps.md       # Atribución por gradientes
│   └── SHAP.md                # Valores de Shapley
│
├── SAPROT/                 # Documentación del modelo SaProt
│   ├── SAPROT.md              # Descripción general del modelo
│   ├── TUTORIAL.md            # Tutorial de uso
│   ├── PAPERS.md              # Papers relacionados
│   ├── LINKS.md               # Enlaces y recursos
│   └── ANÁLISIS/              # Análisis y aplicaciones
│       ├── Score de Mutación SaProt.md  # Fórmulas del score
│       ├── Score LLR.md                 # Análisis de magnitudes
│       └── Explicabilidad SaProt.md     # Técnicas XAI aplicadas
│
├── ESM-3/                  # Documentación del modelo ESM-3
│   ├── ESM-3.md               # Descripción general del modelo
│   └── TUTORIAL.md            # Tutorial de uso
│
├── BITACORA.md             # Registro cronológico de actividades
├── Attachments/            # Imágenes y archivos adjuntos
└── Tags/                   # Sistema de etiquetas
```

## Modelos Estudiados

### SaProt
Modelo de lenguaje para proteínas que incorpora información estructural (3Di/Foldseek) además de la secuencia. Permite predicción zero-shot de efectos de mutaciones.

### ESM-3
Modelo de la familia ESM (Evolutionary Scale Modeling) de Meta AI.

## Conceptos Clave

- **Score de Mutación**: Log-likelihood ratio para evaluar el efecto de variantes
- **3Di**: Alfabeto estructural de 20 caracteres que representa geometría local
- **Foldseek**: Herramienta que convierte estructuras 3D en secuencias de tokens
- **XAI**: Técnicas de explicabilidad (Saliency Maps, SHAP) aplicadas a pLMs

## Herramientas

Este repositorio está organizado como un vault de [Obsidian](https://obsidian.md/) para facilitar la navegación y conexión de conceptos mediante wikilinks.
