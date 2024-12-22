# Informe de salida

## Resumen Ejecutivo

Esta investigación tiene como objetivo implementar y evaluar modelos de aprendizaje automático para la predicción temprana de diabetes en pacientes, utilizando datos médicos y demográficos, con el propósito de apoyar a profesionales de la salud en la toma de decisiones clínicas.

Se exploraron diversos algoritmos de aprendizaje automático para entrenar los modelos y, luego de un análisis exhaustivo de sus métricas de desempeño, se obtuvo que el modelo con mejor desempeño fue el entrenado con el algoritmo [Extreme Gradient Boosting](https://xgboost.readthedocs.io/en/stable/) (XGB).

Las métricas de desempeño utilizadas en el estudio fueron métricas especializadas para evaluar modelos de clasificación, estas son: Accuracy, Precision, Recall y F1-Score. Estas métricas nos indican que el modelo seleccionado genera una excelente predicción de verdaderos positivos (VP), así como verdaderos negativos (VN), sin embargo, los falsos negativos (FN) representan casi una tercera parte del total de la etiqueta 1, lo cual nos indica que existe un sesgo en la clasificación de pacientes con diabetes.

El modelo se desplegó utilizando el servicio de alojamiento web [Railway](https://railway.app/) y el API se creó con el Framework [FastAPI]( https://fastapi.tiangolo.com/).

## Resultados del Proyecto

### Entregables y Logros Alcanzados

**Desarrollo del modelo predictivo:** Se construyó un modelo de Machine Learning utilizando un conjunto de datos obtenidos de Kaggle. Los datos incluían variables clave como género, edad, presión arterial, historial de enfermedades cardíacas, antecedentes de tabaquismo, índice de masa corporal (IMC), niveles de HbA1c y niveles de glucosa en sangres.

**Preprocesamiento de datos:** Se implementó un pipeline de preprocesamiento que incluyó la imputación de valores nulos, la normalización de variables numéricas y la codificación de variables categóricas.

**Entrenamiento y ajuste del modelo:** Se entrenaron múltiples algoritmos de Machine Learning, incluyendo: K-vecinos más cercanos, arboles de decisión, bayesiano ingenuo multinomial, aumento de gradiente externo y redes neuronales multicapa; se utilizó validación cruzada para evitar el sobreajuste.

**Evaluación del modelo:** Se evaluó el desempeño del modelo utilizando métricas como: accuracy, precisión, recall y f1-score.

### Evaluación del Modelo Final y Comparación con el Modelo Base

**Modelo base:** se utilizaron cinco entrenamientos de modelos para validar cuál de ellos se comportaba mejor para este caso de uso:

1. **KNN (K-Nearest Neighbors)**
2. **DT (Decision Tree)**
3. **MNB (Multinomial Naive Bayes)**
4. **XGB (XGBoost)**
5. **MNN (Multilayer Neural Network)**

**Modelo final:** Después de realizar una revisión de hiperparámetros y seleccionar los mejores para cada modelo, se seleccionó el modelo de `XGBoost` que obtuvo en general, el mejor desempeño bajo las métricas utilizadas [Accuracy, Precision, Recall y F1-score](/docs/modeling/model_report.md)

### Descripción de los Resultados y su Relevancia para el Negocio

El modelo predictivo generado sirve como base, para permitir a los profesionales de la salud, identificar de forma temprana los pacientes con mayor riesgo de desarrollar diabetes, lo cual facilita la aplicación de intervenciones preventivas. Esto puede contribuir en la reducción de costos de atención sanitaria y a la mejora de la calidad de vida de los pacientes. Es importante destacar que el modelo es bastante efectivo detectando resultados de falsos verdaderos, sin embargo, tiene oportunidad de mejora clasificando verdaderos positivos.

### Desafíos y Obstáculos

**Desbalance de datos:** La variable objetivo tenia un desbalance significativo, lo cual supuso un reto bastante elevado para obtener buenos resultados en las predicciones de los modelos

**Selección de características:** La identificación de las variables más relevantes para entrenar el modelo fue un reto, ya que la inclusión de variables irrelevantes afectaba la generalización del modelo.

**Ajuste de hiperparámetros:** Se encontró que el ajuste fino de hiperparámetros era esencial para mejorar el rendimiento del modelo.

### Lecciones Aprendidas

**Importancia del preprocesamiento de datos:** La limpieza y preparación de los datos demostró ser fundamental para la construcción del modelo final.

**Extracción de características:** Utilizar técnicas de extracción de características, para convertir todas la variables en numéricas, permitió reducir la dimensionalidad y mejorar la interpretabilidad del modelo.

### Recomendaciones para Futuros Proyectos

**Ampliar la base de datos:** Incorporar datos adicionales de distintas fuentes para mejorar la robustez del modelo podría ayudar a evitar sesgos zonales o poblacionales debido a que en la fuente donde se obtuvieron los datos, no se llega a obtener este nivel de detalle.

**Desarrollar una interfaz de usuario:** Implementar una aplicación de interfaz gráfica que permita a los profesionales de la salud interactuar fácilmente con el modelo predictivo, esto debido a que los usuarios finales no necesariamente tienen el background técnico para utilizar el modelo actualmente implementado con peticiones HTTP.

**Ajustes de hiperparámetros:** Si bien se usó [Optuna](https://optuna.org/) para la selección de los hiperparámetros, al realizar múltiples ejecuciones se obtuvieron distintos valores para los mismos, por lo que se recomendaría aumentar el rango de etapas de entrenamiento para validar si efectivamente los valores seleccionados corresponden a los mejores posibles para el entrenamiento de estos modelos.

## Conclusiones

El modelo muestra un buen desempeño en la predicción de diabetes, especialmente en la identificación de casos negativos. Es necesario mejorar el `recall` para identificar un mayor porcentaje de pacientes con diabetes. Esto podría lograrse mediante el ajuste de `hiperparámetros` experimentando con diferentes valores del modelo o mejorando el desbalanceo de las clases. Adicionalmente se podría analizar la importancia de las características y seleccionar aquellas que sean más relevantes para la predicción de diabetes.