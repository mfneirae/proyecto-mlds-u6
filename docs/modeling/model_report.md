# Reporte del Modelo Final

## Resumen Ejecutivo

Esta investigación tiene como objetivo implementar y evaluar modelos de aprendizaje automático para la predicción temprana de diabetes en pacientes, utilizando datos médicos y demográficos, con el propósito de apoyar a profesionales de la salud en la toma de decisiones clínicas. 

Se exploraron diversos algoritmos de aprendizaje automático para entrenar los modelos y, luego de un análisis exhaustivo de sus métricas de desempeño, se obtuvo que el modelo con mejor desempeño fue el entrenado con el algoritmo [Extreme Gradient Boosting](https://xgboost.readthedocs.io/en/stable/) (XGB). 

Las métricas de desempeño utilizadas en el estudio fueron métricas especializadas para evaluar modelos de clasificación, estas son: Accuracy, Precision, Recall y F1-Score. Estas métricas nos indican que el modelo seleccionado genera una excelente predicción de verdaderos positivos (VP), así como verdaderos negativos (VN), sin embargo, los falsos negativos (FN) representan casi una tercera parte del total de la etiqueta 1, lo cual nos indica que existe un sesgo en la clasificación de pacientes con diabetes.

## Descripción del Modelo

Tomando los resultados de todos los modelos implementados, se optó por tomar como modelo final:

### XGB (XGBoost)

- **Descripción**: Es un algoritmo que realiza una implementación optimizada de otro algoritmo conocido como “Aumento de Gradiente”. Construye múltiples árboles de decisión en secuencia, minimizando el error de los modelos anteriores.
- **Ventajas**: Alta precisión, manejo eficiente de datos desbalanceados y compatibilidad con datos heterogéneos.
- **Desventajas**: Requiere un ajuste cuidadoso de hiperparámetros y puede ser computacionalmente intensivo.
- **Fuente de información para el entrenamiento**: [Diabetes Prediction](https://www.kaggle.com/datasets/iammustafatz/diabetes-prediction-dataset)Corresponde a una colección de datos médicos y demográficos de pacientes, junto con su estado de diabetes (positivo o negativo)

Se utilizo [Optuna](https://optuna.org/) para realizar una búsqueda de los mejores [hiperparámetros](/scripts/training/3_xgb_classifier_model.ipynb) obteniendo los siguientes resultados:

- **max_depth:** 48 (profundidad máxima de cada árbol en el ensamble)
- **n_estimators:** 130 (número de árboles en el ensamble)
- **learning_rate:** 0.010291737939302062 (tasa de aprendizaje, utilizada para reducir el sobreajuste)

## Evaluación del Modelo

![Confusion_Matrix_Xgb](/scripts/training/graphics/confusion_matrix_xgb.jpg)

El modelo seleccionado, correspondiente a XGBoost, es extremadamente preciso en la predicción de VP (pacientes sin diabetes), con una cantidad muy baja de FP (pacientes sanos clasificados con diabetes). Muestra a su vez un buen rendimiento en la predicción de VN (pacientes con diabetes) aunque se presenta una sesgo de casi una tercera parte de la muestra en los FN (pacientes diabéticos clasificados como sanos), no es muy elevada pero esto ocasiona que los resultados obtenidos no sean tan confiables en la detección de la diabetes utilizando el conjunto de datos suministrado, aspecto a considerar a la hora de implementar el modelo.

### Cálculo de Métricas

![Xgb_Model_Metrics](/scripts/training/graphics/xgb_model_metrics.jpg)

**Accuracy:**

**$(VP + VN) / (VP + VN + FP + FN)$** = $(26284 + 1726) / (26284 + 1726 + 14 + 819)$ ≈ **$0.971$**

**Precision:**

**Etiqueta 0** = **$VP / (VP + FN)$** = $26284 / (26284 + 819)$ ≈ **$0.969$**
**Etiqueta 1** = **$VN / (VN + FP)$** = $1726 / (1726 + 14)$ ≈ **$0.992$**

**Recall (Sensibilidad):**

**Etiqueta 0** = **$VP / (VP + FP)$** = $26284 / (26284 + 14)$ ≈ **$0.999$**
**Etiqueta 1** = **$VN / (VN + FN)$** = $1726 / (1726 + 819)$ ≈ **$0.678$**

**F1-score:**

**Etiqueta 0** = **$2 * (precision * recall) / (precision + recall)$** = $(0.969 * 0.999) / (0.969 + 0.999)$ ≈ 0.984$
**Etiqueta 1** = **$2 * (precision * recall) / (precision + recall)$** = $(0.992 * 0.678) / (0.992 * 0.678)$ ≈ 0.806$

### Interpretación de las Métricas

**Accuracy:** El modelo clasifico correctamente el 97.1% de las muestras.

**Precision:** El modelo acierta un 96.9% de la veces a la hora de clasificar a pacientes sin diabetes (etiqueta 0) y un 99.2% para pacientes con diabetes (etiqueta 1).

**Recall:** El modelo clasifico correctamente al 99.9% de los pacientes sin diabetes (etiqueta 0) y al 67.8% de los pacientes con diabetes (etiqueta 1).

**F1-score:** El modelo tiene un balance del 98.4%, entre precisión y recall, para clasificar a pacientes sin diabetes (etiqueta 0) y 80.6% para clasificar a pacientes con diabetes (etiqueta 1). Esto nos indica que es un buen modelo.

Con base en las métricas, el modelo tiene un buen desempeño general, especialmente en términos de `precision`, esto significa que el modelo es muy bueno para identificar correctamente a los pacientes que no tienen diabetes, sin embargo, el `recall` es relativamente bajo para la etiqueta 1, lo que indica que el modelo tiene un ligero sesgo para identificar a todos los pacientes que tienen diabetes.

## Conclusiones y Recomendaciones

El modelo muestra un buen desempeño en la predicción de diabetes, especialmente en la identificación de casos negativos. Es necesario mejorar el `recall` para identificar un mayor porcentaje de pacientes con diabetes. Esto podría lograrse mediante el ajuste de `hiperparámetros` experimentando con diferentes valores del modelo. Adicionalmente se podría analizar la importancia de las características y seleccionar aquellas que sean más relevantes para la predicción de diabetes.

## Referencias

[1] Hastie, T., Tibshirani, R., & Friedman, J. (2009). *The Elements of Statistical Learning*. Springer.

[2] Quinlan, J. R. (1986). Induction of decision trees. *Machine Learning*, 1(1), 81-106.

[3] Murphy, K. P. (2012). *Machine Learning: A Probabilistic Perspective*. MIT Press.

[4] Chen, T., & Guestrin, C. (2016). XGBoost: A scalable tree boosting system. *Proceedings of the 22nd ACM SIGKDD International Conference on Knowledge Discovery and Data Mining*.

[5] Goodfellow, I., Bengio, Y., & Courville, A. (2016). *Deep Learning*. MIT Press.   

[6] Chen, T., & Guestrin, C. (2016). XGBoost: A scalable tree boosting system. *Proceedings of the 22nd ACM SIGKDD International Conference on Knowledge Discovery and Data Mining*.

[7] Kaggle (2022). Diabetes prediction dataset [On Line] available at https://www.kaggle.com/datasets/iammustafatz/diabetes-prediction-dataset1