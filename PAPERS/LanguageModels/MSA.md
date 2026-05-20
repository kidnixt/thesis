Alineamiento de múltiples secuencias de proteínas (o DNA) que permite comparar y visualizar similitudes evolutivas entre proteínas relacionadas.

## Concepto

MSA coloca secuencias homólogas una sobre otra para revelar:
- Posiciones conservadas (ancestrales)
- Posiciones variables (divergentes)
- Gaps (indels evolutivos)
- Patrones de co-variación

```
Proteína1:  MKFLA--DLSLA
Proteína2:  MKFLA--DVSLA
Proteína3:  MKFLNQSDLSLA
Consenso:   MKFLA**D*SLA
```

## Importancia en Biología Comparativa

MSAs revelan:
- **Restricciones funcionales**: posiciones altamente conservadas son críticas
- **Evolución**: pasos de divergencia entre proteínas
- **Estructura**: residuos que contactan probablemente están bajo presión
- **Epistasis**: co-variación puede indicar interacciones estructurales

## Construcción

Métodos comunes:
- **BLAST/PSI-BLAST**: búsqueda de homólogos
- **MUSCLE, MAFFT, ClustalW**: alineamiento progresivo
- **Structure-based alignment**: usando coordenadas 3D

## En métodos clásicos de predicción

Antes del paper sobre language models:
- [[SIFT|SIFT]] utiliza MSA para construir Position Specific Scoring Matrices
- [[EVMutation|EVMutation]] utiliza MSA para estimar [[Potts models|Potts models]]
- [[DeepSequence|DeepSequence]] entrena VAE sobre MSA

## Limitaciones

- **Computacionalmente costoso**: construir MSAs profundas es lento
- **Dependiente de homólogos**: proteínas con pocos homólogos tienen MSAs malas
- **Sesgo taxonómico**: bases de datos suelen ser sesgadas hacia proteínas bien-estudiadas
- **Información incompleta**: MSA solo captura evolución pasada, no predicción de futuro

## En el paper de Language Models

El paper argumenta que los language models entrenados directamente en secuencias pueden capturar información evolutiva **sin necesidad de construir MSAs explícitamente**:

> "Un Transformer suficientemente grande puede aprender esas regularidades directamente desde secuencias sin necesidad de alineamientos explícitos"

Esto es una diferencia conceptual fundamental: del paradigma "MSA + modelo específico por familia" al paradigma "modelo generalista sin MSAs".

## Relación con evolución

La hipótesis fundamental es que:
> la evolución natural contiene información implícita sobre estructura y función

MSA es una representación explícita de esa evolución. Language models aprenden esa información implícitamente.
