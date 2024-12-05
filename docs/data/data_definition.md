# Definición de los datos

## Origen de los datos

El conjunto de  `Diabetes prediction dataset` es una colección de datos médicos y demográficos de pacientes, junto con su estado diabético (positivo o negativo). Los datos incluyen características como la edad, el sexo, el índice de masa corporal (IMC), la hipertensión, las cardiopatías, el historial de tabaquismo, el nivel de HbA1c y el nivel de glucosa en sangre.

Este conjunto de datos puede utilizarse para crear modelos de aprendizaje automático que permitan predecir la diabetes en pacientes basándose en su historial médico y en información demográfica. Esto puede ser útil para que los profesionales sanitarios identifiquen a los pacientes que pueden estar en riesgo de desarrollar diabetes y desarrollen planes de tratamiento personalizados. Además, el conjunto de datos puede ser utilizado por los investigadores para explorar las relaciones entre diversos factores médicos y demográficos y la probabilidad de desarrollar diabetes.

Los datos fuero tomados de [kaggle](https://www.kaggle.com/datasets/iammustafatz/diabetes-prediction-dataset) y estos, a su vez, fueron tomados de [Electronic Health Records (EHRs)](https://www.cms.gov/priorities/key-initiatives/e-health/records) como fuente primaria de información de multiples proveedores de Salud y fueron agrupados, limpieados y preprocesados para garantizar consistencia y eliminar cualquier información incompleta o irrelevante.

## Especificación de los scripts para la carga de datos

### Procedimiento general

![Procedimiento](https://firebasestorage.googleapis.com/v0/b/personalwp-8822c.appspot.com/o/Captura%20de%20pantalla%202024-12-01%20213749.png?alt=media&token=5ec6eb64-81b5-4b88-a7f9-cb900239704a)

#### Paso 1

El archivo original fue descargado directamente desde Kaggle:

[diabetes_prediction_dataset.csv](https://www.kaggle.com/datasets/iammustafatz/diabetes-prediction-dataset)

#### Paso 2

El procedimiento de carga al `storage online` de firebase se hizo de acuerdo a los pasos descritos en la [documentación](https://firebase.google.com/docs/storage/web/upload-files). La información puede ser consultada de la siguiente manera:

[DATOS](https://firebasestorage.googleapis.com/v0/b/personalwp-8822c.appspot.com/o/diabetes_prediction_dataset.csv?alt=media&token=4d70d154-c3d0-4fa0-a3aa-9b9972dd3b95)

#### Paso 3

El script descarga el archivo CSV desde la [URL](https://firebasestorage.googleapis.com/v0/b/personalwp-8822c.appspot.com/o/diabetes_prediction_dataset.csv?alt=media&token=4d70d154-c3d0-4fa0-a3aa-9b9972dd3b95) generada en el paso 2 utilizando `wget`, lo transforma en un DataFrame de pandas, y valida errores comunes, como datos vacíos o problemas de conexión.

El documento completo se puede acceder desde la ruta:

[scripts\data_acquisition\project_charter.ipynb](https://github.com/mfneirae/proyecto-mlds-u6/blob/aada8817809aba2e5e5ce7c0cf339fc52a4f51e8/scripts/data_acquisition/project_charter.ipynb)

La función utilizada se describe a continuación:

```python
  def download_firebase(url, logger): 
    '''
        Extrae la base de datos que fue previamente almacenada en Firebase en un CSV para facilitar su acceso

        Args:
        -----
            url : str
                  URL de acceso público al CSV que contiene la información.

        Returns:
        --------
            pandas df
                   Dataframe con la información extraída.

        Examples:
        ---------
            >>> download_firebase(url)
    '''
      logger.info("Extrayendo el archivo desde Firebase")
      df = None
      try:
          df = pd.read_csv(url)
          logger.info("Archivo cargado")
      except requests.exceptions.RequestException as e:
          logger.info(f"Error al descargar el archivo CSV: {e}")
      except pd.errors.EmptyDataError:
          logger.info("El archivo CSV está vacío.")
      except Exception as e:
          logger.info(f"Ocurrió un error inesperado: {e}")
      return df
```

## Referencias a rutas o bases de datos origen y destino

A continuación, se especifican las rutas o bases de datos de origen y destino para los datos.

### Rutas de origen de datos

#### Ubicación de los archivos de origen de los datos

El documento original se encuentra disponible como [diabetes_prediction_dataset.csv](https://www.kaggle.com/datasets/iammustafatz/diabetes-prediction-dataset) y esta disponible en kaggle de forma gratuita con licencia abierta.

#### Estructura de los archivos de origen de los datos

El archivo está en formato `CSV`, que es compatible con el módulo `pandas` para su análisis y manipulación.

#### Procedimientos de transformación y limpieza de los datos

El script simplemente carga el archivo como un DataFrame de pandas, no es necesaria una transformación ni una limpieza justamente porque ya fue previamente realizada en el momento de consolidar la información, esto según lo indicado directamente en la [documentación del Dataset](https://www.kaggle.com/datasets/iammustafatz/diabetes-prediction-dataset)

### Base de datos de destino

#### Base de datos de destino para los datos

No se menciona una base de datos de destino en el script actual. Los datos se manejan directamente en memoria como un DataFrame.

#### Estructura de la base de datos de destino

Se respeta la estructura original del archivo.

#### Procedimientos de carga y transformación de los datos en la base de datos de destino

Para el procedimiento de carga se propone utilizar [DVC](https://dvc.org/), pese a que el conjunto de datos no cambiará, se propone como una forma de hacer escalable el proyecto para futuras ingestas de datos.
