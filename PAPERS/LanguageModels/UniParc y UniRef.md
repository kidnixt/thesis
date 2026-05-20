Bases de datos públicas de secuencias proteicas que coleccionan información de evolución y diversidad proteica global.

## UniParc (Universal Protein Archive)

- **Propósito**: archivo completo de todas las secuencias proteicas conocidas
- **Contenido**: ~500 millones de secuencias únicas
- **Cobertura**: redundancia eliminada (secuencias idénticas se unifican)
- **Fuentes**: mezcla de UniProt, PDB, NCBI, otras

## UniRef (Non-redundant Reference)

Series de bases de datos a diferentes niveles de similitud:

### UniRef100
- Secuencias 100% idénticas se agrupan
- Incluye todas las secuencias
- Base más granular

### UniRef90
- Agrupa secuencias > 90% de identidad
- Reduce redundancia significativa
- Balance entre cobertura e información

### UniRef50
- Agrupa secuencias > 50% de identidad
- Mayor compresión
- Usado cuando velocidad es crítica

## En el paper de Language Models

El paper utiliza aproximadamente:
```
250 millones de secuencias proteicas
```

Provenientes de UniParc/UniRef, representando:
- Toda la diversidad evolutiva conocida
- Millones de especies
- Diferentes dominios de la vida

Esto es la base del pretraining del modelo.

## Importancia

UniParc/UniRef son cruciales porque:
- **Escala**: dataset masivo necesario para foundation models
- **Diversidad**: cubre toda la evolución conocida
- **Autoridad**: respaldadas por consorcio internacional (EMBL, NCBI, etc.)
- **Actualización**: se mantienen actualizadas regularmente

## Acceso

- Públicamente disponibles
- Descargables en múltiples formatos
- APIs para búsqueda rápida
- En https://www.uniprot.org/

## Cómo se usa en pretraining

1. Descargar todas las secuencias de UniRef
2. Procesar en batches masivos
3. Entrenar modelo de language modeling autoregresivo
4. Resulta en embeddings contextuales de aminoácidos

## Comparación con otros

- **GenBank**: más enfocado en nucleotidos, más desorganizado
- **PDB**: incluye estructura pero mucho más pequeño (~150k proteínas)
- **UniProt**: versión curada/anotada de UniParc, más metadatos

## Limitaciones

- **Sesgo**: base de datos suele estar sesgada hacia proteínas bien-estudiadas
- **Calidad variable**: algunas secuencias pueden tener errores de anotación
- **Representación incompleta**: muchísimas proteínas nunca han sido secuenciadas
- **Contexto faltante**: secuencia sin contexto celular/ambiental
