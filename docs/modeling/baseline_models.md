# Reporte de los Modelos Baseline

Este documento contiene los resultados de los modelos que se utilizaron como baseline.

## Descripción de los modelos

A continuación, se describen los modelos de Machine Learning utilizados, incluyendo su funcionamiento básico y características principales:

### 1. **KNN (k-Nearest Neighbors)**

- **Descripción**: Es un algoritmo basado en la similitud. Para clasificar un dato nuevo, el modelo busca los "k" puntos de datos más cercanos en el espacio y asigna la clase más común entre estos vecinos [1].
- **Ventajas**: Fácil de implementar y entender; funciona bien en problemas donde las clases son separables espacialmente.
- **Desventajas**: Sensible a datos desbalanceados y al ruido en los datos. Su rendimiento disminuye con conjuntos de datos grandes debido a su alta complejidad computacional.

### 2. **DT (Decision Tree)**

- **Descripción**: Construye un árbol de decisiones basado en divisiones secuenciales de los datos utilizando métricas como la ganancia de información o el índice Gini. Cada nodo representa una condición, y las hojas corresponden a las clases [2].
- **Ventajas**: Interpretación intuitiva y capacidad de manejar datos categóricos y continuos.
- **Desventajas**: Puede sobreajustarse fácilmente si no se limita la profundidad del árbol.

### 3. **MNB (Multinomial Naive Bayes)**

- **Descripción**: Modelo probabilístico que asume independencia entre las características. Es adecuado para datos categóricos o de conteo, como texto o frecuencias [3].
- **Ventajas**: Rápido de entrenar, eficiente en términos de memoria y adecuado para datos de alta dimensionalidad.
- **Desventajas**: La suposición de independencia es rara vez verdadera, lo que puede afectar su precisión.

### 4. **XGB (XGBoost)**

- **Descripción**: Implementación optimizada del algoritmo de boosting de gradiente. Construye múltiples árboles de decisión en secuencia, minimizando el error de los modelos anteriores [4].
- **Ventajas**: Alta precisión, manejo eficiente de datos desbalanceados y compatibilidad con datos heterogéneos.
- **Desventajas**: Requiere un ajuste cuidadoso de hiperparámetros y puede ser computacionalmente intensivo.

### 5. **MNN (Multilayer Neural Network)**

- **Descripción**: Red neuronal compuesta por una capa de entrada, una o más capas ocultas y una capa de salida. Utiliza funciones de activación no lineales para aprender representaciones complejas [5].
- **Ventajas**: Capaz de modelar relaciones no lineales y patrones complejos en los datos.
- **Desventajas**: Requiere grandes volúmenes de datos para un buen rendimiento y es sensible a la configuración de hiperparámetros.
  
## Variables de entrada

Las variables de entrada se describen a continuación:

| **Variable** | **Descripción** | **Tipo de dato** | **Rango/Valores posibles** |
|---|---|---|---|
| **gender** | Género del paciente | Categórico (string) | Female, Male, Other |
| **age** | Edad del paciente | Numérico (float) | 102 posibles valores entre 0.08 y 80.0 |
| **hypertension** | Indica si el paciente tiene hipertensión | Categórico (bool) | 0, 1 (0: No, 1: Sí) |
| **heart_disease** | Indica si el paciente tiene una enfermedad cardíaca | Categórico (bool) | 0, 1 (0: No, 1: Sí) |
| **smoking_history** | Antecedentes de tabaquismo del paciente | Categórico (string) | never, No Info, current, former, ever, not current |
| **bmi** | Índice de masa corporal del paciente | Numérico (float) | 4247 posibles valores entre 10.01 y 95.69 |
| **HbA1c_level** | Nivel promedio de glucosa en sangre del paciente (últimos meses) | Numérico (float) | 18 posibles valores entre 3.5 y 9.0 |
| **blood_glucose_level** | Nivel de glucosa en sangre del paciente (en el momento de la prueba) | Numérico (int) | 18 posibles valores entre 80 y 300 |

## Variable objetivo

La variable `diabetes` es una variable categórica con dos posibles valores:

- `0` (etiqueta 0)
- `1` (etiqueta 1)

Esta variable indica si un paciente tiene, o no, diabetes. Se considera esta variable como una variable objetivo, ya que refleja el resultado de interés en el análisis.

La naturaleza de la variable sugiere ser una variable clave del conjunto de datos, ya que estamos interesados en clasificar a los pacientes que puedan desarrollar diabetes

Esta variable tiene la siguiente distribución:

- **`No (etiqueta 0):`** 91.5% de las observaciones.
- **`Sí (etiqueta 1):`** 8.5% de las observaciones.

## Evaluación del modelo

### Métricas de evaluación

#### Matriz de Confusión

Es una tabla que visualiza el desempeño de un modelo comparando las predicciones con los valores reales. Muestra las siguientes categorías:

- Verdaderos Positivos (VP): Predicciones positivas correctas.
- Verdaderos Negativos (VN): Predicciones negativas correctas.
- Falsos Positivos (FP): Predicciones positivas incorrectas (el modelo dijo "sí" cuando era "no").
- Falsos Negativos (FN): Predicciones negativas incorrectas (el modelo dijo "no" cuando era "sí").

Permite analizar qué tipo de errores comete el modelo y en qué medida.

#### Accuracy

Mide la proporción de predicciones correctas (tanto positivas como negativas) del total de predicciones.

$(VP + VN) / (VP + VN + FP + FN)$

Fácil de entender e interpretar pero puede ser engañosa si las clases están desbalanceadas (ej: muchos más casos "no diabetes" que "diabetes").

#### Precision

De todas las veces que el modelo predijo "positivo", ¿cuántas fueron correctas?

$VP / (VP + FP)$

Útil cuando el costo de los falsos positivos es alto (ej: diagnosticar diabetes a alguien sano implica pruebas y tratamientos innecesarios).

#### Recall

De todos los casos realmente "positivos", ¿cuántos logró identificar el modelo?

$VP / (VP + FN)$

Útil cuando el costo de los falsos negativos es alto (ej: no detectar diabetes puede tener consecuencias graves para la salud).

#### F1-score

Es el promedio armónico entre precision y recall.

$2 * (Precision * Recall) / (Precision + Recall)$

Busca un equilibrio entre ambas métricas. Útil cuando se necesita un modelo con buen rendimiento tanto en precision como en recall.

### Resultados de evaluación

#### **DT (Decision Tree)**

![Descripción](/scripts/training/graphics/confusion_matrix_dt.jpg)

**Alta precisión:** El modelo es muy preciso en la detección de casos negativos (no diabetes), como lo demuestra el alto número de VN y la ausencia de FP.

**Falsos negativos:** El modelo tiene algunos falsos negativos, lo que significa que podría pasar por alto algunos casos de diabetes. Esto es algo a tener en cuenta, ya que podría tener implicaciones en la salud de los pacientes.

#### **KNN (k-Nearest Neighbors)**

![Descripción](/scripts/training/graphics/confusion_matrix_knn.jpg)

**Buen rendimiento general:** El modelo KNN tiene un buen rendimiento en la detección de diabetes, con una cantidad considerable de verdaderos negativos y verdaderos positivos.

**Falsos positivos y falsos negativos:** A diferencia del árbol de decisión, KNN tiene falsos positivos, lo que significa que a veces diagnostica diabetes cuando no la hay. También tiene falsos negativos, lo que significa que puede pasar por alto algunos casos de diabetes.

#### **MNB (Multinomial Naive Bayes)**

![Descripción](/scripts/training/graphics/confusion_matrix_mnb.jpg)

**Problemas en la detección de positivos:** El modelo MNB tiene una gran cantidad de falsos negativos, lo que significa que falla en la detección de la mayoría de los casos de diabetes. Esto se refleja en el bajo número de verdaderos positivos.

**Relativamente preciso en casos negativos:** Aunque tiene algunos falsos positivos, MNB es relativamente preciso en la detección de casos negativos (no diabetes).

#### **MNN (Multilayer Neural Network)**

![Descripción](/scripts/training/graphics/confusion_matrix_mnn.jpg)

**Extremadamente desequilibrado:** El modelo MNN está completamente sesgado hacia la predicción de casos positivos (diabetes). Clasifica a todas las personas como diabéticas, sin importar si realmente lo son o no.

**Alto riesgo de falsos positivos:** Este modelo tiene una tasa de falsos positivos extremadamente alta, lo que significa que diagnosticaría diabetes a muchas personas sanas.

**Inútil en la práctica:** En la práctica, este modelo sería inútil para la detección de diabetes, ya que no puede distinguir entre personas con y sin la enfermedad.

#### **XGB (XGBoost)**

![Descripción](/scripts/training/graphics/confusion_matrix_xgb.jpg)

**Excelente precisión en casos negativos:** XGBoost es extremadamente preciso en la detección de casos negativos (no diabetes), con una cantidad muy baja de falsos positivos.

**Buen rendimiento general:** El modelo muestra un buen rendimiento en general, con una cantidad considerable de verdaderos positivos y un número relativamente bajo de falsos negativos.

## Análisis de los resultados

### F1 Score

![Descripción](/scripts/training/graphics/models_f1score.jpg)

#### Interpretación general F1 Score

- **F1-score**: Es una métrica que combina precisión y recall en una sola medida, buscando un equilibrio entre ambas. Es útil cuando se busca un modelo que tenga un buen rendimiento tanto en precisión como en recall. Se obserbva un muy buen rendimiento para los modelos DT y XGB.

### Accuracy

![Descripción](/scripts/training/graphics/models_accuracy.jpg)

#### Interpretación general Accuracy

- **Accuracy**: Es la proporción de predicciones correctas (tanto positivas como negativas) entre el total de predicciones realizadas por el modelo. Es una métrica general que da una idea del rendimiento global del modelo. Todos los modelos, salvo MNN, tienen resultados buenos, se destacan DT y XGB.

### Precision

![Descripción](/scripts/training/graphics/models_Precision.jpg)

#### Interpretación general Precision

- **Precision**: Es la proporción de predicciones positivas correctas (VP) entre todas las predicciones positivas realizadas por el modelo (VP + FP). Indica la capacidad del modelo para evitar falsos positivos (predecir que algo es positivo cuando en realidad es negativo). Se destacan el rendimiento de DT y XGB que obtienen muy buenos resultados para las dos etiquetas.

### Recall

![Descripción](/scripts/training/graphics/models_recall.jpg)

#### Interpretación general Recall

- **Recall**: Es la proporción de predicciones positivas correctas (VP) entre todos los casos realmente positivos (VP + FN). Indica la capacidad del modelo para identificar correctamente todos los casos positivos, evitando falsos negativos (predecir que algo es negativo cuando en realidad es positivo). Todos los modelos, salgo MNN tienen un buen rendimiento para las etiquetas de detección negativa (etiqueta 0) sin embargo MNB y KNN no responden bien ante las detecciones positivas (etiqueta 1).

### Comparación entre Modelos

**KNN, DT y XGB:**

- **Rendimiento sólido:** Muestran un rendimiento consistentemente bueno en todas las métricas, con alta precisión, F1-score, precision y un recall aceptable para ambas etiquetas (0: detección negativa, 1: detección positiva).
- **Equilibrio:** Logran un buen equilibrio entre la detección de casos positivos y negativos, con un ligero sesgo hacia la identificación de casos negativos.
- **Robustez:** Su rendimiento consistente sugiere robustez y confiabilidad para la detección de diabetes.

**MNB:**

- **Debilidad en detección positiva:** Rendimiento inferior en la detección de casos positivos (etiqueta 1) en todas las métricas, especialmente en recall y F1-score.
- **Precisión aceptable en casos negativos:** Precisión y recall aceptables para la etiqueta 0 (casos negativos), pero no sobresalientes.
- **Limitaciones:** Presenta limitaciones para la detección de diabetes, particularmente en la identificación de personas con la enfermedad.

**MNN:**

- **Excelente recall para casos positivos:** Alto recall en la detección de casos positivos (etiqueta 1), superando a los demás modelos.
- **Problemas con casos negativos:** Bajo recall y precisión para la etiqueta 0, tendiendo a clasificar erróneamente a personas sanas como diabéticas.
- **Desequilibrio:** Rendimiento desequilibrado, con enfoque en la detección de casos positivos a expensas de un alto número de falsos positivos.

## Conclusiones

- **DT** y **XGB** son los modelos más efectivos y consistentes para clasificar la detección de la diabbetes para la fuente de información utilizada.
- **KNN** funciona bien para la Etiqueta 0, pero tiene problemas con la Etiqueta 1.
- **MNB** y **MNN** presentan un rendimiento deficiente en al menos una de las etiquetas, lo que sugiere que no son adecuados para este problema sin ajustes adicionales.

## Referencias

[1] Hastie, T., Tibshirani, R., & Friedman, J. (2009). *The Elements of Statistical Learning*. Springer.

[2] Quinlan, J. R. (1986). Induction of decision trees. *Machine Learning*, 1(1), 81-106.

[3] Murphy, K. P. (2012). *Machine Learning: A Probabilistic Perspective*. MIT Press.

[4] Chen, T., & Guestrin, C. (2016). XGBoost: A scalable tree boosting system. *Proceedings of the 22nd ACM SIGKDD International Conference on Knowledge Discovery and Data Mining*.

[5] Goodfellow, I., Bengio, Y., & Courville, A. (2016). *Deep Learning*. MIT Press.
