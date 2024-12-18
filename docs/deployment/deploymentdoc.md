# Despliegue de modelos

## Infraestructura

- **Nombre del modelo:**
  
  DiaBoost

- **Plataforma de despliegue:**

    MLFlow + NGROK (local)

- **Requisitos técnicos:**

  - Python versión: 3.8 o superior
  
  **Bibliotecas de terceros:**
  - xgboost
  - mlflow
  - pandas
  - numpy
  - flask (para la API opcional)
  - pyngrok (para exponer localmente)

- **Requisitos de seguridad:**

  - Usar un token de acceso seguro para NGROK.
  - No exponer información confidencial en los logs.

- **Diagrama de arquitectura:** (imagen que muestra la arquitectura del sistema que se utilizará para desplegar el modelo)

## Código de despliegue

- **Archivo principal:**

``` os
  scripts/deployment/main.py
```

- **Rutas de acceso a los archivos:**

``` os
  scripts/deployment/
```

- **Variables de entorno:**
  - **NGROK_AUTH_TOKEN:** Tu token de NGROK para exponer la URL pública.
  - **MLFLOW_TRACKING_URI:** La URI de la instancia de MLFlow.
  - **PORT:** El puerto en el que se ejecutará la API localmente.

## Documentación del despliegue

- **Instrucciones de instalación:** (instrucciones detalladas para instalar el modelo en la plataforma de despliegue)
- **Instrucciones de configuración:** (instrucciones detalladas para configurar el modelo en la plataforma de despliegue)
- **Instrucciones de uso:** (instrucciones detalladas para utilizar el modelo en la plataforma de despliegue)
- **Instrucciones de mantenimiento:** (instrucciones detalladas para mantener el modelo en la plataforma de despliegue)
