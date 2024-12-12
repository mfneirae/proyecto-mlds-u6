# Reporte de los Modelos Baseline

## Descripción de los Modelos

A continuación, se describen los modelos de Machine Learning utilizados, incluyendo su funcionamiento básico y características principales:

### 1. **KNN (K-Nearest Neighbors)**

- **Descripción**: Es un algoritmo basado en la similitud. Para clasificar un dato nuevo, el modelo busca los ‘k’ puntos de datos más cercanos en el espacio y asigna el dato a la clase más común entre estos vecinos.
- **Ventajas**: Fácil de implementar y entender; funciona bien en problemas donde las clases son separables espacialmente.
- **Desventajas**: Sensible a datos desbalanceados y al ruido en los datos. Su rendimiento disminuye con grandes conjuntos de datos debido a su alta complejidad computacional.

### 2. **DT (Decision Tree)**

- **Descripción**: Es un algoritmo que construye un árbol de decisiones basado en divisiones secuenciales de los datos, utilizando métricas como la ganancia de información o el índice Gini. Cada nodo representa una condición y las hojas corresponden a las clases.
- **Ventajas**: Interpretación intuitiva, buena capacidad para manejar datos categóricos y continuos.
- **Desventajas**: Puede sobreajustarse fácilmente si no se limita la profundidad del árbol.

### 3. **MNB (Multinomial Naive Bayes)**

- **Descripción**: Es un algoritmo probabilístico que asume independencia entre las características. Es adecuado para datos categóricos o de conteo, como texto o frecuencias.
- **Ventajas**: Rápido de entrenar, eficiente en términos de memoria y adecuado para datos de alta dimensionalidad.
- **Desventajas**: La suposición de independencia es rara vez verdadera, lo que puede afectar su precisión.

### 4. **XGB (XGBoost)**

- **Descripción**: Es un algoritmo que realiza una implementación optimizada de otro algoritmo conocido como “Aumento de Gradiente”. Construye múltiples árboles de decisión en secuencia, minimizando el error de los modelos anteriores.
- **Ventajas**: Alta precisión, manejo eficiente de datos desbalanceados y compatibilidad con datos heterogéneos.
- **Desventajas**: Requiere un ajuste cuidadoso de hiperparámetros y puede ser computacionalmente intensivo.

### 5. **MNN (Multilayer Neural Network)**

- **Descripción**: Red neuronal compuesta por una capa de entrada, una o más capas ocultas y una capa de salida. Utiliza funciones de activación no lineales para aprender representaciones complejas.
- **Ventajas**: Capaz de modelar relaciones no lineales y patrones complejos en los datos.
- **Desventajas**: Requiere grandes volúmenes de datos para un buen rendimiento y es sensible a la configuración de hiperparámetros.
  
## Variables de Entrada

Las variables de entrada para todos lo modelos son las siguientes:

- gender
- age
- hypertension
- heart_disease
- smoking_history
- bmi
- HbA1c_level
- blood_glucose_level

**Nota:** Su descripción, tipo de dato y posibles alores se puede encontrar en el siguiente [archivo](/docs/data/data_dictionary.md)

### Hiperparámetros

Los hiperparámetros a explorar, para cada modelo, son los siguientes:

- **KNN:** n_neighbors
- **DT:** max_depth
- **MNB:** alpha
- **XGB:** max_depth, n_estimators y learning_rate
- **MNN:** units, activation, dropout y learning_rate

## Variable Objetivo

La variable `diabetes` es una variable categórica con dos posibles valores:

- `0` (Etiqueta 0: No tiene diabetes)
- `1` (Etiqueta 1: Si tiene diabetes)

Esta variable indica si un paciente tiene, o no, diabetes y tiene la siguiente distribución:

- **`Etiqueta 0:`** 91.5% de las observaciones.
- **`Etiqueta 1:`** 8.5% de las observaciones.

## Evaluación de los Modelos

### Métricas de Evaluación

#### Matriz de Confusión

Es una tabla que permite visualizar el desempeño de un modelo, comparando las predicciones con los valores reales. Muestra las siguientes categorías:

- **Verdaderos Positivos (VP):** Predicciones positivas correctas.
- **Verdaderos Negativos (VN):** Predicciones negativas correctas.
- **Falsos Positivos (FP):** Predicciones positivas incorrectas (El modelo predijo "0" cuando era "1").
- **Falsos Negativos (FN):** Predicciones negativas incorrectas (El modelo predijo "1" cuando era "0").

Esto permite analizar qué tipo de errores comete un modelo y en qué medida.

#### Accuracy

Mide la proporción que existe entre las predicciones correctas (VP y VN) y el total de predicciones.

**$(VP + VN) / (VP + VN + FP + FN)$**

Fácil de entender e interpretar pero puede ser engañosa si las clases están desbalanceadas (Ej: Más casos de "no diabetes" que de "diabetes" o viceversa).

#### Precision

Proporción de todas las clasificaciones positivas del modelo que realmente son positivas

**$VP / (VP + FP)$**

Útil cuando el costo de los FP es alto.

#### Recall

Proporción de todos los positivos reales que se clasificaron correctamente como positivos

**$VP / (VP + FN)$**

Útil cuando el costo de los FN es alto.

#### F1-score

Es el promedio armónico entre `Precision` y `Recall`.

**$2 * (Precision * Recall) / (Precision + Recall)$**

Busca un equilibrio entre ambas métricas. Útil cuando se necesita un modelo con buen rendimiento tanto en `Precision` como en ` Recall `.

### Resultados de Evaluación

#### **KNN (K-Nearest Neighbors)**

![Confusion_Matrix_Knn](/scripts/training/graphics/confusion_matrix_knn.jpg)

**Rendimiento general:** El modelo muestra un buen rendimiento en la clasificación de pacientes con o sin diabetes, con una cantidad considerable de VN y VP.

**Falsos positivos y falsos negativos:** Se evidencian FP, lo que significa que a veces diagnostica diabetes cuando no la hay, sin embargo, la proporción es mínima por lo que no es demasiado preocupante. Se evidencian FN, lo que significa que puede pasar por alto algunos casos de diabetes; esta proporción si es elevada por lo que es importante tener en cuenta métricas como: `Precision`, ` Recall ` y ` F1-Score` a la hora de comparar con otros modelos. 

#### **DT (Decision Tree)**

![Confusion_Matrix_Dt](/scripts/training/graphics/confusion_matrix_dt.jpg)

**Rendimiento general:** El modelo es extremadamente preciso en la clasificación de pacientes con “no diabetes”, como lo demuestra el alto número de VP y la ausencia de FP.

**Falsos negativos:** Se evidencian FN, lo que significa que podría pasar por alto algunos casos de diabetes; esta proporción no es muy elevada, pero si representa una tercera parte de la muestra, por lo que es importante tener en cuenta métricas como: `Precision`, ` Recall ` y ` F1-Score` a la hora de comparar con otros modelos.

#### **MNB (Multinomial Naive Bayes)**

![Confusion_Matrix_Mnb](/scripts/training/graphics/confusion_matrix_mnb.jpg)

**Rendimiento general:** El modelo tiene poca cantidad de VN, lo que significa que falla en la clasificación de pacientes con diabetes. 

**Falsos positivos y falsos negativos:** Este modelo puede ser descartado debido a su alto número de FN, esto indica que es un modelo deficiente para la clasificación de pacientes con diabetes (objetivo del proyecto)

#### **XGB (XGBoost)**

![Confusion_Matrix_Xgb](/scripts/training/graphics/confusion_matrix_xgb.jpg)

**Rendimiento general:** El modelo muestra un buen rendimiento en la clasificación de pacientes con o sin diabetes, con una cantidad considerable de VN y VP, además de ser muy preciso en la clasificación de pacientes con “no diabetes”, como lo demuestra el alto número de VP y la muy baja cantidad de FP.

**Falsos positivos y falsos negativos:** Se evidencian FP, lo que significa que a veces diagnostica diabetes cuando no la hay, sin embargo, la proporción es mínima por lo que no es demasiado preocupante. Se evidencian FN, lo que significa que podría pasar por alto algunos casos de diabetes; esta proporción no es muy elevada, pero si representa una tercera parte de la muestra, por lo que es importante tener en cuenta métricas como: `Precision`, ` Recall ` y ` F1-Score` a la hora de comparar con otros modelos.

#### **MNN (Multilayer Neural Network)**

![Confusion_Matrix_Mnn](/scripts/training/graphics/confusion_matrix_mnn.jpg)

**Rendimiento general:** El modelo está completamente en la clasificación de pacientes con o sin diabetes. Clasifica a todas las personas como diabéticas, sin importar si realmente lo son.

**Falsos positivos:** Este modelo puede ser descartado debido a su alto número de FP, esto indica que diagnosticaría diabetes a muchos pacientes sanos. En la práctica, este modelo sería inútil para la detección de diabetes, ya que no puede distinguir entre personas con y sin la enfermedad.

## Análisis y Comparación de los Resultados

### Resultados Accuracy

![Models_Accuracy](/scripts/training/graphics/models_accuracy.jpg)

#### Interpretación

- **Accuracy**: Es una métrica general que da una idea del rendimiento general de los modelos. Nos permite observar que todos los modelos, salvo MNN, tienen resultados buenos de predicción (sin tener en cuenta el desbalance de clases), destacando principalmente los modelos entrenados con DT y XGB.

### Resultados Precision

![Models_Precision](/scripts/training/graphics/models_precision.jpg)

#### Interpretación

- **Precision**: Es una métrica que indica la capacidad del modelo para evitar FP (predecir que algo es positivo cuando en realidad es negativo). Nos permite observar que los modelos entrenados con KNN, DT y XGB obtienen muy buenos resultados para las dos etiquetas, destacando principalmente DT y XGB con métricas similares.

### Resultados Recall

![Models_Recall](/scripts/training/graphics/models_recall.jpg)

#### Interpretación general Recall

- **Recall**: Es una métrica que indica la capacidad del modelo para identificar correctamente todos los casos positivos, evitando FN (predecir que algo es negativo cuando en realidad es positivo). Todos los modelos, salvo MNN tienen un buen rendimiento para la etiqueta 0, sin embargo MNB y KNN no tienen un buen rendimiento para la etiqueta 1. En este sentido, destacando principalmente DT y XGB sin tener tampoco unas métricas demasiado elevadas para la etiqueta 1.

### Resultados F1-Score

![Models_F1score](/scripts/training/graphics/models_f1score.jpg)

#### Interpretación

- **F1-score**: Es una métrica que combina precisión y recall en una sola medida, buscando un equilibrio entre ambas. Es útil cuando se busca un modelo que tenga un buen rendimiento tanto en precisión como en recall. Se observa un muy buen rendimiento para los modelos DT y XGB.

### Comparación Entre Modelos

**KNN, DT y XGB:**

- **Rendimiento sólido:** Estos modelos muestran un rendimiento consistentemente bueno en todas las métricas (accuracy, precision, recall y f1-score) para ambas etiquetas, destacando principalmente XGB ya que su f1-score es un poco mas elevado con respecto a los otros dos modelos (aunque el modelo DT esta extremadamente cerca en cuanto a rendimiento)
- **Equilibrio:** Estos modelos logran un buen equilibrio entre la detección de VP y VN, con un ligero sesgo hacia la identificación de VP.
- **Robustez:** Su rendimiento consistente sugiere robustez y confiabilidad para la detección de diabetes.

**MNB:**

- **Debilidad en detección positiva:** Este modelo muestra tener un rendimiento deficiente en la detección de VN (etiqueta 1), sus métricas son sumamente bajas, salvo el accuracy, lo que nos lleva a descartar el modelo.
- **Precisión aceptable en detección negativa:** Precisión y recall aceptables para los VP (etiqueta 0), pero no sobresalientes.
- **Limitaciones:** Presenta limitaciones para la clasificación de diabetes, particularmente en la identificación de personas con la enfermedad.

**MNN:**

- **Problemas en detección negativa:** Baja precision y recall para los VP (etiqueta 0), tendiendo a clasificar erróneamente a pacientes sanos como diabéticos.
- **Excelente detección positiva:** Alto recall en la detección de VN (etiqueta 1), superando a los demás modelos, sin embargo, esto se da porque no logra identificar los VP (etiqueta 0) lo que nos lleva a descartar el modelo.
- **Limitaciones:** Presenta limitaciones para la clasificación de diabetes, particularmente en la identificación de personas sin la enfermedad.

## Conclusiones

- **DT** y **XGB** son los modelos más efectivos y consistentes para clasificar la detección de la diabetes para la fuente de información utilizada, resaltando **XGB** por tener métricas ligeramente mejores que **DT**
- **KNN** funciona bien para la etiqueta 0, pero tiene ligeros problemas con la etiqueta 1.
- **MNB** y **MNN** presentan un rendimiento deficiente en al menos una de las etiquetas, lo que sugiere que no son adecuados para este problema.

## Referencias

Todos los modelos fueron entrenados utilizando algoritmos provenientes de la libreria [Scikit-Learn]( https://scikit-learn.org/stable/). `Scikit-Learn` es una biblioteca de código abierto para aprendizaje automático en Python. Ofrece una amplia gama de algoritmos y técnicas para el análisis de datos y la construcción de modelos de aprendizaje automático. Esta libreria proporciona una amplia documentación y una comunidad activa de desarrolladores y usuarios. La biblioteca se utiliza ampliamente en la industria y en la investigación para la construcción y evaluación de modelos de aprendizaje automático. 
