# Reporte del Modelo Final

## Resumen Ejecutivo

Esta investigación tiene como objetivo desarrollar y evaluar modelos de aprendizaje automático para la predicción temprana de diabetes utilizando datos médicos y demográficos. El objetivo es implementar un sistema de Machine Learning capaz de predecir si un paciente puede desarrollar diabetes a partir de datos médicos y demográficos, con el propósito de apoyar a profesionales de la salud en la toma de decisiones clínicas. Se explorararon diversos algoritmos de aprendizaje automático, incluidos métodos de conjunto que indicaron que el modelo con mejor desempeño fue [Extreme Gradient Boosting](https://xgboost.readthedocs.io/en/stable/) (XGB). El estudio utilizó métricas de evaluación rigurosas que indicaron que, como resultado, se genera una excelente predicción de verdaderos negativos, sin embargo, los falsos positivos hacen que el modelo no tenga un buen desempeño en la predicción de casos positivos de diabetes.

## Descripción del Problema

La diabetes es una de las enfermedades crónicas más comunes, la cual afecta a millones de personas a nivel global. Su diagnóstico tardío genera altos costos médicos y, adicionalmente,  reduce la calidad de vida de los pacientes. Los sistemas de salud necesitan soluciones tecnológicas, capaces de apoyar el proceso de identificación temprana del desarrollo de esta enfermedad en los pacientes, con el fin de apoyar al profesional en la generación de un mejor diagnostico del paciente y así anticipar un posible deterioro en su salud del mismo al no detectar a tiempo dicha enfermedad.

El diagnóstico tardío de la diabetes, frecuentemente detectada en etapas avanzadas, sumado a la limitación de recursos médicos para el análisis masivo de datos y la fragmentación de la información de los pacientes, representan desafíos significativos para la intervención temprana. Esta problemática se traduce en un aumento de las complicaciones de la enfermedad, mayores costos para los sistemas de salud y una disminución en la calidad de vida de los pacientes. La falta de integración de la información y la capacidad limitada para realizar análisis predictivos dificultan la identificación temprana de individuos en riesgo, impidiendo la implementación de medidas preventivas y tratamientos oportunos.

En este contexto, el aprendizaje automático emerge como una herramienta poderosa para transformar el abordaje de la diabetes. Al permitir la construcción de sistemas predictivos a partir de grandes volúmenes de datos médicos y demográficos, se ofrece la posibilidad de asistir a los profesionales médicos en la evaluación de riesgos en poblaciones extensas. Esta capacidad predictiva no solo contribuye a la reducción de los costos asociados a las complicaciones de la diabetes mediante la intervención temprana, sino que también proporciona herramientas escalables y accesibles para diversas instituciones de salud, democratizando el acceso a un diagnóstico más preciso y oportuno.

## Descripción del Modelo

Tomando los resultados de todos los modelos implementados, se optó por tomar como modelo final:

### XGB (XGBoost)

- **Descripción**: Implementación optimizada del algoritmo de boosting de gradiente. Construye múltiples árboles de decisión en secuencia, minimizando el error de los modelos anteriores [1].
- **Ventajas**: Alta precisión, manejo eficiente de datos desbalanceados y compatibilidad con datos heterogéneos.
- **Desventajas**: Requiere un ajuste cuidadoso de hiperparámetros y puede ser computacionalmente intensivo.
- **Fuente de información** [Diabetes prediction dataset] que corresponde a una colección de datos médicos y demográficos de pacientes, junto con su estado de diabetes (positivo o negativo) (https://www.kaggle.com/datasets/iammustafatz/diabetes-prediction-dataset) [2]

Utilizando [Optuna](https://optuna.org/) se hizo una [búsqueda de los mejores hiperparámetros](/scripts/training/3_xgb_classifier_model.ipynb) obteniendo los siguientes resultados:

- **max_depth:** 48 (profundidad máxima de cada árbol en el ensamble)
- **n_estimators:** 130 (número de árboles en el ensamble)
- **learning_rate:** 0.010291737939302062 (tasa de aprendizaje, utilizada para reducir el sobreajuste)

## Evaluación del Modelo

![Descripción](/scripts/training/graphics/confusion_matrix_xgb.jpg)

El modelo escogido, correspondiente a XGBoost es extremadamente preciso en la detección de casos negativos (no diabetes), con una cantidad muy baja de falsos positivos. Muestra un buen rendimiento en general, con una cantidad considerable de verdaderos positivos y un número relativamente bajo de falsos negativos. Sin embargo, en la predicción de falsos positivos tenemos un número considerable que hace que los resultados obtenidos no sean tan confiables en la detección de la diabetes utilizando el conjunto de datos suministrado.

### Cálculo de Métricas

**Accuracy (Precisión):**

$(TP + TN) / (TP + FP + FN + TN) = (26284 + 1726) / (26284 + 14 + 819 + 1726) ≈ 0.958$

**Precision:**

$TP / (TP + FP) = 1726 / (1726 + 14) ≈ 0.992$

**Recall (Sensibilidad):**

$TP / (TP + FN) = 1726 / (1726 + 819) ≈ 0.676$

**Specificity (Especificidad):**

$TN / (TN + FP) = 26284 / (26284 + 819) ≈ 0.969$

**F1-score:**

$2 * (precision * recall) / (precision + recall) ≈ 0.807$

### Interpretación de las Métricas

**Accuracy:** El modelo clasifica correctamente el 95.8% de las muestras.

**Precision:** Cuando el modelo predice diabetes, tiene razón en un 99.2% de los casos.

**Recall:** El modelo identifica correctamente el 67.6% de los casos reales de diabetes.

**Specificity:** El modelo identifica correctamente el 96.9% de los casos donde no hay diabetes.

**F1-score:** El resultado obtenido indica que existe un buen balance entre precisión y recall.

Basado en las métricas, el modelo tiene un buen desempeño general, especialmente en términos de precisión y especificidad. Esto significa que el modelo es muy bueno para identificar correctamente a los pacientes que no tienen diabetes. Sin embargo, el recall es relativamente bajo, lo que indica que el modelo no es tan bueno para identificar a todos los pacientes que tienen diabetes.

## Conclusiones y Recomendaciones

El modelo muestra un buen desempeño en la predicción de diabetes, especialmente en la identificación de casos negativos. Es necesario mejorar el recall para identificar un mayor porcentaje de pacientes con diabetes. Esto podría lograrse mediante el ajuste de hiperparámetros experimentando con diferentes valores del modelo. Adicionalmente se podría  analizar la importancia de las características y seleccionar aquellas que sean más relevantes para la predicción de diabetes.

## Referencias

[1] Chen, T., & Guestrin, C. (2016). XGBoost: A scalable tree boosting system. *Proceedings of the 22nd ACM SIGKDD International Conference on Knowledge Discovery and Data Mining*.

[2] Kaggle (2022). Diabetes prediction dataset [On Line] available at https://www.kaggle.com/datasets/iammustafatz/diabetes-prediction-dataset1   

