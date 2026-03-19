Proceso de crear nuevas [[Proteína]]s o modificar existentes para obtener [[Función de proteínas|funciones]] específicas.

## Enfoques del diseño

### De novo design
Crear proteínas completamente nuevas:
- Sin basarse en proteínas naturales
- Diseñar desde cero la [[Secuencia de aminoácidos]] y/o [[Estructura de proteínas|estructura]]
- Herramientas: Rosetta, modelos generativos

### Diseño guiado por estructura
Empezar con una estructura objetivo:
- **Inverse folding**: dada una estructura, generar secuencias compatibles
- Útil para crear proteínas que adopten formas específicas
- SaProt tiene esta capacidad

### Diseño guiado por función
- Optimizar para una función específica
- Combinar con predicción de [[Efecto de mutaciones]]
- Iterativo: diseñar → predecir → seleccionar

## Desafíos

- Explorar el vasto [[Espacio de secuencias proteicas]]
- Balancear múltiples propiedades ([[Estabilidad proteica]], [[Solubilidad de proteínas|solubilidad]], función)
- Validar experimentalmente los diseños

## En modelos computacionales

Los [[Modelo de lenguaje de proteínas]] revolucionan el diseño:
- Generan secuencias "realistas" (dentro del [[Espacio de proteínas]] natural)
- Pueden optimizar múltiples propiedades simultáneamente
- Reducen el espacio de búsqueda experimental

Ver [[SAPROT/TUTORIAL|Tutorial de SaProt]] — la sección **Diseño de secuencias (inverse folding)** permite generar secuencias a partir de estructuras.