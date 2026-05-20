Base de datos pública que contiene información sobre actividades bioquímicas de moléculas pequeñas contra targets proteicos.

## Contenido

ChEMBL recopila:
- ~2 millones de moléculas únicas
- ~18 millones de bioactividades medidas
- Targets proteicos diversos
- Datos experimentales de literatura científica

## Propiedades representadas

- **Potencia**: IC50, Ki, EC50
- **Selectividad**: perfiles sobre múltiples targets
- **Propiedades fisicoquímicas**: LogP, solubilidad, etc.
- **Datos de toxicidad y ADMET**

## En Drug Discovery

ChEMBL es un recurso fundamental para:
- Identificar hits iniciales
- Entender relaciones [[SAR|SAR]] conocidas
- Benchmarking de modelos predictivos
- Validación de nuevos candidatos

## En DrugLLM

DrugLLM utiliza ChEMBL como fuente de datos para:
- Construir trayectorias de modificación molecular
- Obtener datos de actividades biológicas de targets conocidos
- Evaluación en zero-shot y few-shot sobre targets no vistos durante pretraining
- Success rates de ~0.76 en targets Ki/IC50 desconocidos

El paper menciona que muchos benchmarks biológicos de DrugLLM dependen de modelos predictivos auxiliares (ChemProp) en lugar de mediciones wet-lab reales, lo que es una limitación importante a reconocer.

## Acceso

ChEMBL es de acceso público y disponible en:
- https://www.ebi.ac.uk/chembl/
- Descargas en múltiples formatos
- APIs programáticas

## Relación con ZINC

Mientras que [[ZINC|ZINC]] es principalmente una colección de moléculas drug-like para virtual screening, ChEMBL es una base de datos de bioactividades. Muchos trabajos utilizan ambas:
- ChEMBL para actividades biológicas
- ZINC para ampliar el espacio molecular con moléculas sintetizables
