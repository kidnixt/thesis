Predicción de qué residuos aminoacídicos en una proteína están espacialmente cercanos en la estructura 3D, basándose únicamente en información de secuencia y evolución.

## Concepto

Dos aminoácidos que están en contacto estructural (< ~8 Å de distancia en 3D):
- Típicamente co-evolucionan (si uno cambia, el otro también)
- Presentan co-variación estadística en [[MSA|alineamientos]]
- Un contact prediction identifica estos pares

## Método clásico

Utilizar co-variación en MSA:
- Si dos posiciones co-evolucionan fuertemente → probablemente en contacto
- [[Potts models|Potts models]] pueden estimar coupling strengths $J_{ij}$
- Altos $|J_{ij}|$ → posible contacto

## Importancia

Contact prediction es valioso porque:
- **Estructura sin difracción**: predecir estructura desde secuencia
- **Validación estructural**: corroborar modelos de estructura
- **Desambiguación**: resolver pliegues ambiguos

## En relación con Foundation Models

El paper demuestra que los attention heads de un [[Transformer|Transformer]] entrenado en secuencias proteicas naturalmente aprenden:

> "ciertas heads aprenden contactos estructurales reales aun sin supervisión estructural explícita"

Esto es un hallazgo extremadamente importante históricamente.

Implica que:
- La evolución codifica información estructural
- Los language models capturan esa información implícitamente
- No se necesita supervisión explícita de estructura

## Conexión con trabajos posteriores

Este hallazgo inspiró trabajos posteriores:
- **MSA Transformer**: refina este enfoque usando MSAs explícitas
- **ESMFold**: combina embeddings PLM con módulos de predicción de estructura
- **OmegaFold**: arquitectura alternativa

## En el paper

El paper muestra correlación entre:
- Attention weights de ciertos heads
- Contactos estructurales reales (de PDB)
- Una correlación significativa emerge sin supervisión

Esto fue sorprendente y paradigm-shifting.

## Limitaciones

- **No perfecta**: correlación es fuerte pero no perfecta
- **Depende del head**: no todos los attention heads aprenden contactos
- **Resolución limitada**: contactos predichos pueden ser ruidosos

## Relación con Embedding de proteínas

Los embeddings contextuales de un PLM capturan:
- Información de secuencia local
- Patrones co-evolutivos
- Restricciones estructurales

Todo implícitamente, sin supervisión.
