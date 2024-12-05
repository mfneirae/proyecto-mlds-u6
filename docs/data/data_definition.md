# Definición de los Datos

## Origen de los Datos

Este conjunto de datos es una colección de datos médicos y demográficos de pacientes, junto con una etiqueta que indica si el paciente tiene o no diabetes. Los datos incluyen características como la edad, el sexo, el índice de masa corporal (IMC), la hipertensión, las cardiopatías, el historial de tabaquismo, el nivel de HbA1c y el nivel de glucosa en sangre.

El entrenamiento de un modelo de Machine Learning con estos datos puede ser útil para que los profesionales sanitarios identifiquen a los pacientes que pueden estar en riesgo de desarrollar diabetes y desarrollen planes de tratamiento personalizados. Además, el conjunto de datos puede ser utilizado por los investigadores para explorar las relaciones entre diversos factores médicos y demográficos y la probabilidad de desarrollar diabetes.

Estos datos provienen originalmente de [Electronic Health Records (EHRs)](https://www.cms.gov/priorities/key-initiatives/e-health/records); de allí fueron tomados, agrupados, procesados y republicados en [Kaggle](https://www.kaggle.com/datasets/iammustafatz/diabetes-prediction-dataset).

## Especificación de los Scripts para la Carga de Datos

### Procedimiento

![Procedimiento](https://firebasestorage.googleapis.com/v0/b/personalwp-8822c.appspot.com/o/Captura%20de%20pantalla%202024-12-01%20213749.png?alt=media&token=5ec6eb64-81b5-4b88-a7f9-cb900239704a)

- **Paso 1:** Se descargo el archivo `.csv` desde [Kaggle](https://www.kaggle.com/datasets/iammustafatz/diabetes-prediction-dataset)
- **Paso 2:** Se cargo el [archivo](https://firebasestorage.googleapis.com/v0/b/personalwp-8822c.appspot.com/o/diabetes_prediction_dataset.csv?alt=media&token=4d70d154-c3d0-4fa0-a3aa-9b9972dd3b95) al `Storage Online` de `Firebase` siguiendo los pasos descritos en su [documentación](https://firebase.google.com/docs/storage/web/upload-files).
-  **Paso 3:** Se creo un [script](https://github.com/mfneirae/proyecto-mlds-u6/blob/master/scripts/data_acquisition/project_charter.ipynb) en el cual se descarga el archivo `.csv` desde `Firebase` (utilizando ‘wget’) y se transforma en un DataFrame de pandas, haciendo a su vez una validación de errores como: datos vacíos o problemas de conexión.

## Rutas de Origen de Datos

- **Fuente original:** [Electronic Health Records (EHRs)](https://www.cms.gov/priorities/key-initiatives/e-health/records);
- **Fuente de recopilación:** [Kaggle](https://www.kaggle.com/datasets/iammustafatz/diabetes-prediction-dataset).
- **Fuente de acceso:** [Firebase](https://firebasestorage.googleapis.com/v0/b/personalwp-8822c.appspot.com/o/diabetes_prediction_dataset.csv?alt=media&token=4d70d154-c3d0-4fa0-a3aa-9b9972dd3b95)

El archivo disponible desde la fuente de acceso se encuentra en formato `.csv`, que es compatible con el módulo `pandas` para su análisis y manipulación.

### Procedimientos de Transformación y Limpieza de los datos

…