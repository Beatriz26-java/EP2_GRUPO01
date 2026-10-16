**Equipo:** E01

## P1 – Power BI
Antes de filtrar con el segmentador, el déficit total es de 286,90 mil kWh y la cobertura porcentual es de 90.88 %.  La medida que no puede obtenerse sumando déficits netos globales es el déficit energético total. Ya que el restar los totales (demanda_total_kwh –  energía_total_kwh = 233.243,12 kwh) produce un déficit neto donde el excedente de unas sedes tapa el faltante de otras; siendo el déficit real 286,90 mil kwh. El segmentador altera el contexto del cálculo porque filtra las filas de las tablas antes de que las medidas DAX se apliquen, cuando se selecciona una sola región, las medidas ya no suman las 9 sedes, sino solamente las sedes de esa región, y se recalculan los KPIs solo para la región seleccionada.

## P2 – ArcGIS
De un total de 9 sedes, se validaron 8 sedes de los cuales cumplieron los criterios establecidos de Latitud y Longitud (latitud 13 a 15, longitud –91 a –87), excluyendo la sede con sede_id S09 la cual no cumplía la Longitud establecida (longitud –67). La sede con mayor déficit válido es la sede S04 (Solar San Salvador) el registro de déficit válido es de 77336.41 kWh. Mostrar coordenadas erróneas en mapas conlleva a un gran riesgo, comprometiendo la planeación operativa, la asignación de recursos y la precisión del análisis territorial el cual se basa el proyecto.
Enlace Mapa_Vista1: https://www.arcgis.com/apps/mapviewer/index.html?webmap=a0f0e98746f948cba6fed9e287c49368
Enlace Mapa_Vista2: https://www.arcgis.com/apps/mapviewer/index.html?webmap=4be6975bbd7942cd9271bed4358951c4

## P3 – Reportería
Al generar el informe solo cambia la fecha de generación, pues el script y la plantilla no se modifican manualmente; los KPIS, el grafico, el hallazgo y el sha256_fuente solo variarían si el CSV cambia, manteniendo las mismas columnas. Al compararlo con el dashboard de Power BI, concuerdan deficit_total_kwh (286,904.20), energia_total_kwh (2,913,623.55) y demanda_total_kwh (3,146,866.67), con una cobertura de 90.88%. La principal limitación del caso es que el informe cubre solamente 180 días de datos sintéticos, por lo que nos sirve únicamente como prototipo, y muestra donde se encuentra el déficit de energía, no las razones por las que ocurre. 

## P4 – Predicción
En la prueba realizada del 2026-05-26 al 2026-06-29 el MAE del baseline fue 1.194,57 kWh y el obtenido por la regresión lineal 298,77 kWh obteniendo una mejora del 74,99 %, así que el modelo sí agrega valor. No debe entrenarse con el futuro porque sería una fuga de información: usaría datos que no existen al pronosticar e inflaría las métricas; por eso la división es cronológica y media_movil_7 usa shift(1). El uso real exige contar con la demanda de ayer, la de hace 7 días y el evento programado, y solo se validó en 35 días con un modelo lineal. El error medio sigue siendo de unos 300 kWh, por ende, solo es una estimación, pero no es una certeza. 

## Video Explicativo
https://liveitcaedu-my.sharepoint.com/:v:/g/personal/isela_quintanilla25_itca_edu_sv/IQBzIvaK3lLoSZ3iYgcjkRVBAbTIREpj4VyBFpyXqUfv_8g?nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJPbmVEcml2ZUZvckJ1c2luZXNzIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXciLCJyZWZlcnJhbFZpZXciOiJNeUZpbGVzTGlua0NvcHkifX0&e=YKyWBU.
