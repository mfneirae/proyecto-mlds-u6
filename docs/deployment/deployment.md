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

- **Instrucciones de Configuración:** (instrucciones detalladas para configurar el modelo en la plataforma de despliegue)
- **Instrucciones de Uso:** (instrucciones detalladas para utilizar el modelo en la plataforma de despliegue)
- **Instrucciones de Mantenimiento:** (instrucciones detalladas para mantener el modelo en la plataforma de despliegue)
