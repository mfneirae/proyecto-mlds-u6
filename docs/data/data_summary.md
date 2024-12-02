# Reporte de Datos

Este documento contiene los resultados del análisis exploratorio de datos.

## Resumen general de los datos

|Campo             |Conteo   |Promedio  |Desviación Estándar|min  |25%  |50%  |75%  |max  |
|-------------------|--------|----------|-------------------|-----|-----|-----|-----|-----|
|age                |100000.0|41.885856 |22.516839871617023 |0.08 |24.0 |43.0 |60.0 |80.0 |
|hypertension       |100000.0|0.07485   |0.2631504702289164 |0.0  |0.0  |0.0  |0.0  |1.0  |
|heart_disease      |100000.0|0.03942   |0.1945930169980995 |0.0  |0.0  |0.0  |0.0  |1.0  |
|bmi                |100000.0|27.3207671|6.636783416648369  |10.01|23.63|27.32|29.58|95.69|
|HbA1c_level        |100000.0|5.527507  |1.0706720918835437 |3.5  |4.8  |5.8  |6.2  |9.0  |
|blood_glucose_level|100000.0|138.05806 |40.708136048704134 |80.0 |100.0|140.0|159.0|300.0|
|diabetes           |100000.0|0.085     |0.27888308976662174|0.0  |0.0  |0.0  |0.0  |1.0  |



## Resumen de calidad de los datos

En esta sección se presenta un resumen de la calidad de los datos. Se describe la cantidad y porcentaje de valores faltantes, valores extremos, errores y duplicados. También se muestran las acciones tomadas para abordar estos problemas.

## Variable objetivo

La variable objetivo diabetes tiene la siguiente distribución:

* `No (0)` 91.5% de las observaciones.
* `Sí (1)` 8.5% de las observaciones.

## Variables individuales

En esta sección se presenta un análisis detallado de cada variable individual. Se muestran estadísticas descriptivas, gráficos de distribución y de relación con la variable objetivo (si aplica). Además, se describen posibles transformaciones que se pueden aplicar a la variable.

## Ranking de variables

En esta sección se presenta un ranking de las variables más importantes para predecir la variable objetivo. Se utilizan técnicas como la correlación, el análisis de componentes principales (PCA) o la importancia de las variables en un modelo de aprendizaje automático.

## Relación entre variables explicativas y variable objetivo

En esta sección se presenta un análisis de la relación entre las variables explicativas y la variable objetivo. Se utilizan gráficos como la matriz de correlación y el diagrama de dispersión para entender mejor la relación entre las variables. Además, se pueden utilizar técnicas como la regresión lineal para modelar la relación entre las variables.
