# Reporte de Datos

## Resumen General de los Datos

1. Cuenta con un total de 100.000 registros y cada uno corresponde a una serie de datos médicos y demográficos de un pacientes
2. El conjunto de datos se encuentra en formato de valores separados por comas (CSV) y se transforma en un DataFrame de Pandas para su análisis
3. Pesa 3.7MB y al cargarlo en el NoteBook ocupa un total de 6.9+MB en memoria
4. El espacio utilizado en memoria por el DataFrame es de 17.31MB
5. Cuenta con 9 columnas: 3 de tipo flotante, 4 de tipo entero y 2 de tipo objeto (o cadena)
6. No cuenta con datos faltantes en ninguno de los registros
7. Cuenta con 5 variables categorías y 4 numéricas

## Variable Objetivo

La variable "diabetes" es una variable categórica con dos posibles valores:

- 0
- 1

Esta variable indica si un paciente tiene, o no, diabetes. Se considera esta variable como una variable objetivo, ya que refleja el resultado de interés en el análisis.

La naturaleza de la variable sugiere ser una variable clave del conjunto de datos, ya que estamos interesados en clasificar a los pacientes que puedan desarrollar diabetes

Esta variable tiene la siguiente distribución:

- **`No (0):`** 91.5% de las observaciones.
- **`Sí (1):`** 8.5% de las observaciones.

## Resumen de Calidad de los Datos

- **Datos Faltantes:** No se encontraron datos faltantes en ninguna de las columnas del conjunto de datos como se puede evidenciar en este [archivo](/scripts/preprocessing/missing_data.ipynb)
- **Datos Duplicados:** Se encontraron 3.854 registros duplicados en el conjunto de datos por lo que se procedió a eliminarlos haciendo uso de la función “drop_duplicates” de Pandas. El proceso se puede evidenciar en este [archivo](/scripts/preprocessing/duplicate_data.ipynb)
- **Datos Atipicos:** Se encontraron valores atípicos en las variables “bmi”, “HbA1c_level” y “blood_glucose_level”, sin embargo estos valores no se consideran errores de medición, sino que representan información válida pero excepcional, a pesar de esto, es importante eliminar del conjunto de datos los casos más extremos que pueden generar un sesgo en el análisis, por lo cual se procede a utilizar el criterio del Rango Intercuartílico (IQR) para seleccionar los outliers más extremos. Con esta técnica se encontraron solo 3 registros con outliers extremos en la columna “bmi” los cuales fueron eliminados. El proceso se puede evidenciar en este [archivo](/scripts/preprocessing/atypical_data.ipynb)

**Generalidades:**

- Se identificaron 3.854 registros con valores duplicados y fueron eliminados.
- Se identificaron 3 registro con valores atípicos y fueron eliminados.
- Los datos eliminados representan el 3.9% de los registros del conjunto de datos; este porcentaje es mínimo y no afecta el análisis que se pretende realizar
- En general se observa que el conjunto de datos cuenta con una buena calidad en sus datos

## Variables Individuales

### Variable ‘gender’

Esta distribuida de la siguiente manera:

| **Valor** | **Cantidad** | **Porcentaje** |
|---|---|---|
| Female | 56.161 | 58.4% |
| Male | 39.964 | 41.6% |
| Other | 18 | 0.01% |

#### Graficas ‘gender’

| **Histograma** | **Pie** |
|---|---|
| ![Hist_Gender](/scripts/preprocessing/graphics/hist/hist_gender.jpg) | ![Pie_Gender](/scripts/preprocessing/graphics/pie/pie_gender.jpg) |

### Variable ‘age’

Esta distribuida de la siguiente manera:

| **Frecuencia** | **Valor** | **Cantidad** |
|---|---|---|
| **Mínima** | 0.08 | 36 |
| **Máxima** | 80.00 | 4.932 |

#### Grafica ‘age’

| **Histograma** |
|---|
| ![Hist_Age](/scripts/preprocessing/graphics/hist/hist_age.jpg) |

### Variable ‘hypertension’

Esta distribuida de la siguiente manera:

| **Valor** | **Cantidad** | **Porcentaje** |
|---|---|---|
| 0 | 88.682 | 92.2% |
| 1 | 7.461 | 7.8% |

#### Graficas ‘hypertension’

| **Histograma** | **Pie** |
|---|---|
| ![Hist_Hypertension](/scripts/preprocessing/graphics/hist/hist_hypertension.jpg) | ![Pie_Hypertension](/scripts/preprocessing/graphics/pie/pie_hypertension.jpg) |

### Variable ‘heart_disease’

Esta distribuida de la siguiente manera:

| **Valor** | **Cantidad** | **Porcentaje** |
|---|---|---|
| 0 | 92.220 | 95.9% |
| 1 | 3.923 | 4.1% |

#### Graficas ‘heart_disease’

| **Histograma** | **Pie** |
|---|---|
| ![Hist_Heart_disease](/scripts/preprocessing/graphics/hist/hist_heart_disease.jpg) | ![Pie_Heart_disease](/scripts/preprocessing/graphics/pie/pie_heart_disease.jpg) |

### Variable ‘smoking_history’

Esta distribuida de la siguiente manera:

| **Valor** | **Cantidad** | **Porcentaje** |
|---|---|---|
| never | 34.397 | 35.8% |
| No info | 32.885 | 34.2% |
| former | 9.299 | 9.7% |
| current | 9.197 | 9.6% |
| not current | 6.367 | 6.6% |
| ever | 3.998 | 4.2% |

#### Graficas ‘smoking_history’

| **Histograma** | **Pie** |
|---|---|
| ![Hist_Smoking_history](/scripts/preprocessing/graphics/hist/hist_smoking_history.jpg) | ![Pie_Smoking_history](/scripts/preprocessing/graphics/pie/pie_smoking_history.jpg) |

### Variable ‘bmi’

Esta distribuida de la siguiente manera:

| **Frecuencia** | **Valor** | **Cantidad** |
|---|---|---|
| **Mínima** | 88.76 | 1 |
| **Máxima** | 27.32 | 21.666 |

#### Grafica ‘bmi’

| **Histograma** |
|---|
| ![Hist_Bmi](/scripts/preprocessing/graphics/hist/hist_bmi.jpg) |

### Variable ‘HbA1c_level’

Esta distribuida de la siguiente manera:

| **Frecuencia** | **Valor** | **Cantidad** |
|---|---|---|
| **Mínimo** | 7.0 | 633 |
| **Máximo** | 6.6 | 8.164 |

#### Grafica ‘HbA1c_level’

| **Histograma** |
|---|
| ![Hist_HbA1c_level](/scripts/preprocessing/graphics/hist/hist_HbA1c_level.jpg) |

### Variable ‘blood_glucose_level’

Esta distribuida de la siguiente manera:

| **Frecuencia** | **Valor** | **Cantidad** |
|---|---|---|
| **Mínimo** | 220 | 600 |
| **Máximo** | 159 | 7.478 |

#### Grafica ‘blood_glucose_level’

| **Histograma** |
|---|
| ![Hist_Blood_glucose_level](/scripts/preprocessing/graphics/hist/hist_blood_glucose_level.jpg) |

### Variable ‘diabetes’

Esta distribuida de la siguiente manera:

| **Valor** | **Cantidad** | **Porcentaje** |
|---|---|---|
| 0 | 87.661 | 91.2% |
| 1 | 8.482 | 8.8% |

#### Graficas ‘diabetes’

| **Histograma** | **Pie** |
|---|---|
| ![Hist_Diabetes](/scripts/preprocessing/graphics/hist/hist_diabetes.jpg) | ![Pie_Diabetes](/scripts/preprocessing/graphics/pie/pie_diabetes.jpg) |

## Relación entre Variables Explicativas y Variable Objetivo

1. En la matriz de correlación se pudo observar que existe una correlación lineal media entre algunas variables:
    - ‘age’ y ‘bmi’
    - ‘age’ y ‘diabetes’
    - ‘bmi’ y ‘diabetes’
    - ‘HbA1c_level’ y ‘diabetes’
    - ‘blood_glucose_level’ y ‘diabetes’
2. En la prueba de coeficiente de correlación de Spearman se evidencia que todas las variables están correlacionadas, arrojando en todas las pruebas, un p-valor de 0.000
3. Al graficar los datos, se puede observar también la correlación existente entre todas las variables
4. Se puede evidenciar que existe correlación lineal y no lineal entre las variables del conjunto de datos evidenciando una buena correlación con la variables objetivo

**Nota:** Todo el análisis de correlación se puede evidenciar en el siguiente [archivo](/scripts/preprocessing/relation_between_variables.ipynb)
