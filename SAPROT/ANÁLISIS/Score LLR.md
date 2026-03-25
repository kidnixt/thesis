### 1. La métrica LLR y el rango dinámico

En el paper original de **SaProt (Su et al., 2024)** y en su predecesor **ESM-1v (Meier et al., 2021)**, el _score_ es un **Log-Likelihood Ratio (LLR)**.

- **Referencia:** _Meier, J., et al. (2021). "Language models enable zero-shot prediction of the effects of mutations on protein function"._
- **Justificación:** En este estudio, se observa que las mutaciones con scores LLR cercanos a 0 (entre 0 y -2) suelen solaparse con variantes que en experimentos biológicos resultan ser **benignas o neutrales**. El "ruido" al que me refería es la **varianza de predicción**: el modelo puede asignar pequeñas penalizaciones por cuestiones de entrenamiento del corpus, pero que no representan un cambio estructural real.
    

### 2. Comparación de magnitudes (Escala logarítmica)

Si el LLR está en base $e$ (natural), la probabilidad relativa se calcula como $P_{rel} = e^{score}$.

- Para **-1.30**: $e^{-1.30} \approx 0.27$. La variante es un **27%** tan probable como el WT.
- Para **-7.33**: $e^{-7.33} \approx 0.0006$. La variante es un **0.06%** tan probable como el WT.
- **Conclusión técnica:** Un score de -1.30 indica que el modelo "ve" la mutación como algo menos frecuente, pero no imposible. Un score de -7.33 indica que el modelo la considera **estadísticamente inexistente** en su espacio latente.

