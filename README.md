# marco-datos-tic
Marco de trabajo para la operativización de datos de la brecha digital en Colombia, producidos por el DANE para ser consumidos por un dashboard de Power BI
# Brecha Digital Colombia

Proyecto ETL en lenguaje M (Power Query) para analizar datos de brecha digital en Colombia, a partir de los datos oficiales del DANE.

## 📁 Contenido

- **`/data`**: Archivos fuente descargados (CSV, Excel, etc.) en su estado original (raw)
- **`/m-code`**: Scripts en lenguaje M con la lógica de extracción, transformación y carga
- **`/dashboard`**: Archivo .pbix de Power BI con los dashboards y visualizaciones

## 🚀 Uso Detallado

### Opción 1: Usar solo el código M (desde cero)

Para aplicar las transformaciones a datos descargados de [DANE - ndicadores básicos de TIC en Hogares - Históricos](https://www.dane.gov.co/index.php/estadisticas-por-tema/tecnologia-e-innovacion/tecnologias-de-la-informacion-y-las-comunicaciones-tic/indicadores-basicos-de-tic-en-hogares/informacion-historica) a partir del año 2019:

1. **Abrir Power BI Desktop**
2. **Obtener datos** → Carpeta (o Texto/CSV) y selecciona el archivo que está en `/data`
3. **Abrir el Editor de Power Query** (Transformar datos)
4. **Generar consulta en blanco** (Obtener datos)
5. **Reemplazar el código generado**:
   - En el panel izquierdo, seleccionar la consulta
   - Ir a la barra de fórmulas o al Editor Avanzado (vista Inicio → Editor avanzado)
   - Copiar y pegar TODO el contenido del archivo `.m` que está en `/m-code`
   - Ajustar la ruta del archivo en el tercer paso: ORQUESTACIÓN PRINICIPAL (en la variable RutaArchivo, línea 150)
6. **Aplicar los cambios** (Cerrar y aplicar)
7. **Ajustar la ruta del archivo para cada tabla que se vaya a cargar**

### Opción 2: Usar el archivo .pbix completo

Para ver el resultado final con todos los datos ya transformados:

1. Abrir el archivo `/dashboard/brecha_digital.pbix` directamente en Power BI Desktop
2. Explorar las pestañas y visualizaciones
3. Actualizar con nuevos datos:
   - Ir a Transformar datos
   - En el paso inicial de cada consulta, cambiar la ruta del archivo fuente
   - Refrescar

### Entendiendo el código M

Los archivos en `/m-code` contienen:

- **Pasos de extracción**: Lectura de archivos CSV/Excel desde la carpeta `/data`
- **Transformaciones**: Limpieza, filtrado, cambios de tipo, columnas calculadas
- **Carga**: Estructura final que se carga al modelo de Power BI

Cada paso en M está numerado y comentado con la función que hace cada línea.

### Entendiendo el Dashboard (Power BI)

El dashboard presenta 5 páginas para visualizar las diferentes dimensiones de la brecha digital, además de análisis geográfico y demográfico:

**Dimensión 1 de infraestructura y tenencia:** Se agrupan los módulos referentes a la posesión de activos físicos (tablas C.1, C.2, C.5). Se analiza la disponibilidad de dispositivos como computador de escritorio/portátil o teléfono inteligente.

**Dimensión 2 de comportamiento:** Describe la dinámica de interacción entre el usuario y la tecnología (tablas C.3, C.4, C.8, C.9, C.10). Analiza cómo, dónde y con qué frecuencia se conectan las personas, permitiendo perfilar los hábitos de consumo digital y la intensidad de uso en la vida cotidiana.

**Dimensión 3 de cualidad y apropiación:** Aquí se encuentra el núcleo del análisis de productividad digital (tablas C.6, C16/18) que analizan las actividades de uso y las competencias técnicas, evaluando si la tecnología se utiliza para el desarrollo económico y educativo o para actividades de ocio.

**Dimensión 4 de barreras y brecha digital:** Los indicadores de las tablas C.11, C.12 y C.13 examinan las razones explícitas de los hogares para no acceder a las TIC, clasificándolas en barreras económicas, de cobertura o culturales.

**Dimensión 5 de caracterización y demografía:** Los indicadores de las tablas C.14 y C.15 permiten segmentar la brecha digital según género, edad, nivel educativo y ubicación geográfica, evidenciando las desigualdades sociales.


Este trabajo fue desarrollado como trabajo de grado para la Especialización en Analítica de Datos de CUN Por:

_Autores:_

- Mónica Díaz Barbosa
- Diego Pontón Ramos

2026

