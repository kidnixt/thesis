Técnica electrofisiológica experimental que permite medir corrientes iónicas a través de membranas celulares con resolución de un único canal iónico.

## Historia y origen

Desarrollada por Erwin Neher y Bert Sakmann a mediados de los 1970s. Ganaron el Premio Nobel en 1991 por este trabajo.

## Principio

Utiliza un microelectrodo de vidrio (punta ~1 micrón) que se sella contra una membrana celular:
- Forma un sello de alta resistencia (giga-sello, Giga-Ω)
- Permite medir corrientes muy pequeñas
- Aislamiento de canales individuales

## Configuraciones

### Whole-cell
- Mide corrientes totales de la célula
- Usado para drogas que afectan canales iónicos
- Resolución: pico-amperios (pA)

### Single-channel
- Mide corrientes de un canal único
- Resolución más alta
- Más difícil de realizar

### Patch-clamp clásico
- Electrodo en superficie de célula
- Mide interacciones locales

## En la validación de DrugLLM

Los compuestos HCN2-M1 y HCN2-M2 fueron evaluados usando:
- **Patch-clamp whole-cell**
- **Células HEK293** (células renales embrionarias humanas modificadas)
- **Medida de IC50** (concentración inhibitoria 50%)

Resultados:
- HCN2-M1 e HCN2-M2 mostraron IC50 ~3 veces menor que ivabradina (la molécula de referencia)
- Confirma que el model generó inhibidores funcionales reales

## Ventajas

- **Resolución extremadamente alta**: detecta nanoscorrientes
- **Especificidad**: mide exactamente el target deseado
- **Información dinámica**: captura cinética de canales
- **Cuantitativo**: produce números absolutos de actividad

## Limitaciones

- **Técnicamente difícil**: requiere práctica y especialización
- **Tiempo-consumo**: pocas moléculas pueden testerse rápidamente
- **No escalable**: no es compatible con high-throughput screening
- **Célula-dependiente**: resultados pueden variar con contexto celular

## En Drug Discovery

Patch-clamp es gold standard para:
- Validación de targets iónicos
- Caracterización farmacológica detallada
- Estudios mecanísticos
- Pero no para screening inicial (demasiado lento)

La presencia de datos de patch-clamp experimental es lo que hace válido el claims de DrugLLM de que generó moléculas funcionales reales.
