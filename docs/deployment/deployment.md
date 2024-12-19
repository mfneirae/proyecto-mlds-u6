# Despliegue de Modelos

## Infraestructura

- **Nombre del Modelo:** `diabetes-production-2036`
- **Plataforma de Despliegue:** El despliegue del API se realizó en el servicio de alojamiento web [Railway](https://railway.app/) ya que este se integra de manera sencilla con el [repositorio]( https://github.com/jroncanciot/diabetes) donde se encuentra el API, facilitando el despliegue con muy pocos pasos. El API se creó con el Framework [FastAPI]( https://fastapi.tiangolo.com/) ya que este permite crear endpoints de manera sencilla. 
- **Requisitos Técnicos:** 
  - **Request:** $2.32.3$
  - **Logging:** $0.5.1.2$
  - **Joblib:** $1.4.2$
  - **Pandas:** $2.2.2$
  - **Numpy:** $1.26.4$
  - **Sklearn:** $1.5.2$
  - **Xgboost:** $2.1.3$
  - **Fastapi:** $0.115.6$
- **Requisitos de Seguridad:** Se espera que solo tengan acceso al API las personas pertenecientes al directorio activo de los hospitales y/o clínicas donde se implemente la solución, por ende, se espera que el sistema cuente con un servicio de autenticación previo al consumo del modelo, el cual este conectado a dicho directorio activo para proteger el acceso al modelo; a su vez, la solución se implementa para será accedida únicamente por protocolo HTTPS.
- **Diagrama de Arquitectura:** 

![Api_Architecture](/scripts/evaluation/graphics/api_architecture.png)

## Código de Despliegue

- **Archivos Principales:** Los archivos necesarios para el despliegue del modelo se encuentran dentro de este [repositorio](https://github.com/jroncanciot/diabetes). El archivo que se encarga de la creación del API es el [main.py]( https://github.com/jroncanciot/diabetes/blob/master/main.py) y el que se encarga de la configuración del servidor de alojamiento es el [railway.json]( https://github.com/jroncanciot/diabetes/blob/master/railway.json)
- **Rutas de Acceso a los Archivos:** Todos los archivos se encuentran dentro de la carpeta raiz del proyecto
  - **main.py:** En este archivo se encuentra toda la configuración del API: Clases de entrada y salida, carga del modelo y definición del endpoint de acceso. Puede ser consultado en esta [ruta](https://github.com/jroncanciot/diabetes/blob/master/main.py)
  - **model.joblib:** En este archivo se encuentra el modelo entrenado para hacer las predicciones. Puede ser consultado en esta [ruta](https://github.com/jroncanciot/diabetes/blob/master/model.joblib)
  - **railway.json:** En este archivo se encuentra la configuración base del servidor de alojamiento web. Puede ser consultado en esta [ruta](https://github.com/jroncanciot/diabetes/blob/master/railway.json)
  - **requirements.txt:** En este archivo se encuentran los paquetes necesarios para poder utilizar el API. Puede ser consultado en esta [ruta](https://github.com/jroncanciot/diabetes/blob/master/requirements.txt)
- **Variables de Entorno:**
  - **"GITHUB":** Almacena la URL junto con el token para poder conectar con el repositorio de GitHub y asi poder leer y escribir sobre el mismo

## Documentación del Despliegue

- **Instrucciones de Configuración:** 

  **Configuración FastAPI:**

    Crear un [script](https://github.com/jroncanciot/diabetes/blob/master/main.py) (`main.py`) con las siguientes consideraciones para construir el API:
      
      - 1 Definir el `request` (clase de entrada) y el `response` (clase de salida) del API
      - 2 Cargar el modelo entrenado haciendo uso de `joblib`
      - 3 Definir un endpoint de tipo `post` para consumir el API
      - 4 Construir una función asíncrona para el endpoint, encargada de recibir la petición del usuario (`request`) y retornar la predicción del modelo (`response`)

  **Configuración Railway:**

    - 1 Crear un [archivo](https://github.com/jroncanciot/diabetes/blob/master/railway.json) (`railway.json`) con la configuración básica para la construcción y despliegue del servicio de alojamiento web del API
    - 2 Crear un [archivo](https://github.com/jroncanciot/diabetes/blob/master/requirements.txt) (requirements.txt) que contenga los dependencias necesarias para el funcionamiento del API; dependencias que serán instaladas en el servicio de alojamiento web.

  **Despliegue:**

    - 1 Cargar los archivos (`main.py`, `model.joblib`, `railway.json` y `requirements.txt`) en un [repositorio](https://github.com/jroncanciot/diabetes) de GitHub
    - 2 Crear un nuevo proyecto en [Railway](https://railway.app/)
    - 3 En la creación del proyecto, seleccionar la opción de **“Deploy from GitHub repo”** (despliegue desde un repositorio de GitHub)
    - 4 Seleccionar el repositorio donde se cargaron los archivos del API
    - 5 Generar un dominio para consumir el API en la opción **”Generate Domain”** que se encuentra dentro de la configuración del API desplegada
- **Instrucciones de Uso:**
  Enviar una petición al dominio que fue asignado al API con los siguientes argumentos:
    - **“Método:”** `post`
    - **Url:** `https://diabetes-production-2036.up.railway.app`
    - **Endpoint:** `diabetes_prediction`
    - **Request:** `{"features": […, …, …, …, …, …, …, …]}`

  **cURL de ejemplo:**

  ```
  curl --location 'https://diabetes-production-2036.up.railway.app/diabetes_prediction' \
  --header 'Content-Type: application/json' \
  --data '{
      "features": [
          1.0,
          50.0,
          1.0,
          1.0,
          0.0,
          27.32,
          6.2,
          130.0
      ]
  }'
  ```

  **Nota:** Esta petición puede realizarse con cualquier tecnología de desarrollo. Para `Python`, por ejemplo, se puede utilizar la librería `requests` y construir la petición con los parámetros indicados anteriormente.
- **Instrucciones de Mantenimiento:** Se espera realizar una revisión bimensual del modelo, con el fin de evidenciar si existe ‘drifts’ en los datos. Se pretende hacer uso del paquete [Evidently AI](https://www.evidentlyai.com/) con el fin de detectar tres tipos de drift: Label Drift, Feature Drift y Concept Drift. Adicional a esto, se espera realizar pruebas de A/B Testing, con nuevos modelos entrenados, con el fin de identificar si es necesario reemplazar el modelo implementado 
