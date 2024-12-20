# Informe de salida

## Resumen Ejecutivo

Esta investigación tiene como objetivo implementar y evaluar modelos de aprendizaje automático para la predicción temprana de diabetes en pacientes, utilizando datos médicos y demográficos, con el propósito de apoyar a profesionales de la salud en la toma de decisiones clínicas.

Se exploraron diversos algoritmos de aprendizaje automático para entrenar los modelos y, luego de un análisis exhaustivo de sus métricas de desempeño, se obtuvo que el modelo con mejor desempeño fue el entrenado con el algoritmo [Extreme Gradient Boosting](https://xgboost.readthedocs.io/en/stable/) (XGB).

Las métricas de desempeño utilizadas en el estudio fueron métricas especializadas para evaluar modelos de clasificación, estas son: Accuracy, Precision, Recall y F1-Score. Estas métricas nos indican que el modelo seleccionado genera una excelente predicción de verdaderos positivos (VP), así como verdaderos negativos (VN), sin embargo, los falsos negativos (FN) representan casi una tercera parte del total de la etiqueta 1, lo cual nos indica que existe un sesgo en la clasificación de pacientes con diabetes.

El modelo se desplegó utilizando en el servicio de alojamiento web [Railway](https://railway.app/) y el API se creó con el Framework [FastAPI]( https://fastapi.tiangolo.com/).

## Resultados del proyecto

### Entregables y logros alcanzados

Desarrollo del modelo predictivo: Se construyó un modelo de machine learning utilizando un conjunto de datos obtenidos de Kaggle. Los datos incluían variables clave como edad, género, índice de masa corporal (IMC), historial de enfermedades cardíacas, tabaquismo, niveles de glucosa y HbA1c, y presión arterial.

Preprocesamiento de datos: Se implementó un pipeline de preprocesamiento que incluyó la imputación de valores nulos, la normalización de variables numéricas y la codificación de variables categóricas.

Entrenamiento y ajuste del modelo: Se entrenaron múltiples algoritmos de machine learning, incluyendo regresión logística, árboles de decisión y bosques aleatorios, utilizando validación cruzada para evitar el sobreajuste.

Evaluación del modelo: Se evaluó el desempeño del modelo utilizando métricas como precisión, sensibilidad, especificidad y área bajo la curva ROC (AUC-ROC).

### Evaluación del modelo final y comparación con el modelo base

**Modelo base:** se utilizaron cinco entrenamientos de modelos para validar cuál de ellos se comportaba mejor para este caso de uso:

1. **KNN (K-Nearest Neighbors)**
2. **DT (Decision Tree)**
3. **MNB (Multinomial Naive Bayes)**
4. **XGB (XGBoost)**
5. **MNN (Multilayer Neural Network)**

**Modelo final:** Después de realizar un ajuste de hiperparámetros, se seleccionó el modelo de `Xgboost` que obtuvo en general, el mejor desempeño bajo las métricas utilizadas de [Accuracy, Precision, Recall y F1-score](docs\modeling\model_report.md)

### Descripción de los resultados y su relevancia para el negocio

El modelo predictivo generado sirve como base para permitir a los profesionales de la salud identificar de forma temprana a los pacientes con mayor riesgo de desarrollar diabetes, lo que facilita la aplicación de intervenciones preventivas. Esto puede contribuir a la reducción de costos de atención sanitaria y a la mejora de la calidad de vida de los pacientes. Es de destacar que el modelo es bastante efectivo detectando resultados de falsos verdaderos, sin embargo, tiene oportunidad de mejora clasificando verdaderos positivos.

### Desafíos y obstáculos

**Selección de características:** La identificación de las variables más relevantes para el modelo fue un reto, ya que la inclusión de variables irrelevantes afectaba la generalización del modelo.

**Ajuste de hiperparámetros:** Se encontró que el ajuste fino de hiperparámetros era esencial para mejorar el rendimiento del modelo.

### Lecciones aprendidas

**Importancia del preprocesamiento de datos:** La limpieza y preparación de los datos demostró ser fundamental para el modelo.

**Selección de características:** Utilizar técnicas de selección de características permitió reducir la dimensionalidad y mejorar la interpretabilidad del modelo.

### Recomendaciones para futuros proyectos

**Ampliar la base de datos:** Incorporar datos adicionales de distintas fuentes para mejorar la robustez del modelo podría ayudar a evitar sesgos zonales o poblacionales debido a que en la fuente de kaagle no se llega a obtener este nivel de detalle.

**Desarrollar una interfaz de usuario:** Implementar una aplicación de interfaz gráfica que permita a los profesionales de la salud interactuar fácilmente con el modelo predictivo debido a que los usuarios finales no necesariamente tienen el background técnico para desplegar el modelo actualmente implementado.

**Ajustes de hiperparámetros:** Si bien se usó [Optuna](https://optuna.org/) para la selección de los hiperparámetros, al realizar múltiples ejecuciones se obtuvieron distintos valores para los mismos, por lo que se recomendaría aumentar el rango de etapas de entrenamiento para validar si efectivamente los valores seleccionados corresponden a los mejores posibles para las métricas utilizadas.

## Impacto del proyecto

- Descripción del impacto del modelo en el negocio o en la industria.
- Identificación de las áreas de mejora y oportunidades de desarrollo futuras.

## Conclusiones

El modelo muestra un buen desempeño en la predicción de diabetes, especialmente en la identificación de casos negativos. Es necesario mejorar el `recall` para identificar un mayor porcentaje de pacientes con diabetes. Esto podría lograrse mediante el ajuste de `hiperparámetros` experimentando con diferentes valores del modelo. Adicionalmente se podría analizar la importancia de las características y seleccionar aquellas que sean más relevantes para la predicción de diabetes.
