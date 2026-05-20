Método que utiliza Variational Autoencoders (VAE) entrenados sobre [[MSA|alineamientos múltiples]] para predecir efectos de mutaciones capturando modelos implícitos de coevolución.

## Concepto

DeepSequence entrena un VAE sobre MSA:

1. **Encoder**: comprime MSA en espacio latente
2. **Latent space**: representa información implícita de co-evolución
3. **Decoder**: reconstruye MSA
4. **Mutation scoring**: mutaciones que disminuyen probabilidad de reconstrucción → deletéreas

## Ventaja sobre métodos anteriores

- **Captura no-linealidades**: VAE puede modelar interacciones complejas de orden superior
- **Menos restricciones**: no asume forma funcional específica (como Potts models)
- **Flexible**: puede capturar patrones arbitrarios aprendidos desde datos

## En el paper de Language Models

DeepSequence es el baseline más sofisticado de métodos clásicos:
- Captura interacciones de orden superior
- VAE permite modelado flexible
- Sigue siendo proteína-específico (requiere entrenar por familia)
- Requiere MSAs (aunque potencialmente menos profundas que EVMutation)

PLM supera a DeepSequence, demostrando que:
- Aprendizaje en escala masiva > modelos específicos más sofisticados
- Sin MSAs > con MSAs (al menos en este escenario)

## Limitaciones

- **Computacionalmente costoso**: entrenar VAE por proteína es caro
- **MSA-dependencia**: todavía requiere alineamientos
- **Family-specific**: no generaliza
- **Variabilidad**: resultados pueden depender de inicialización VAE

## Relación conceptual

- **SIFT**: estadística simple, independencia de posiciones
- **EVMutation**: modelos gráficos (Potts), interacciones de orden 2
- **DeepSequence**: deep learning, interacciones arbitrarias
- **Language models**: paradigma completamente distinto, generalista

## Contexto histórico

DeepSequence fue una innovación importante demostrando que deep learning podía mejorar métodos evolutivos clásicos.

Pero el paper de language models sugiere que cambiar el paradigma completamente (de family-specific a general-purpose) es más potente que simplemente haciendo métodos specific más sofisticados.
