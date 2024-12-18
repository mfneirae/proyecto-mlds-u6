# Project Charter - Entendimiento del Negocio

## Nombre del Proyecto

Implementación Ágil de un Sistema de Machine Learning para la Predicción de Diabetes.

## Objetivo del Proyecto

Implementar un sistema de Machine Learning capaz de predecir si un paciente puede desarrollar diabetes a partir de datos médicos y demográficos, con el propósito de apoyar a profesionales de la salud en la toma de decisiones clínicas.

### Objetivos Específicos

1. Explorar el conjunto de datos para entender las relaciones entre las variables disponibles (edad, género, IMC, hipertensión, etc.) y el estado de diabetes
2. Entrenar modelos de clasificación utilizando diferentes técnicas de Machine Learning 
3. Implementar técnicas de validación cruzada y ajuste de hiperparámetros para maximizar el rendimiento de los modelos.
4. Evaluar los modelos entrenados utilizando métricas de desempeño 

## Trasfondo del Negocio

### Contexto

La diabetes es una de las enfermedades crónicas más comunes, la cual afecta a millones de personas a nivel global. Su diagnóstico tardío genera altos costos médicos y, adicionalmente,  reduce la calidad de vida de los pacientes. Los sistemas de salud necesitan soluciones tecnológicas, capaces de apoyar el proceso de identificación temprana del desarrollo de esta enfermedad en los pacientes, con el fin de apoyar al profesional en la generación de un mejor diagnostico del paciente y así anticipar un posible deterioro en su salud del mismo al no detectar a tiempo dicha enfermedad.

### Problema

1. **Diagnóstico Tardío:** Frecuente detección en etapas avanzadas.
2. **Recursos Limitados:** Insuficiente personal médico para análisis masivos.
3. **Fragmentación de Datos:** Falta de integración y análisis predictivo efectivo.

### Oportunidad

El uso de Machine Learning permite construir sistemas predictivos que:

* Ayuden a profesionales médicos a evaluar riesgos en grandes poblaciones.
* Reduzcan costos asociados con complicaciones de diabetes.
* Provean herramientas escalables y accesibles para diversas instituciones.

### Mercado Objetivo

1. Sistemas de salud públicos y privados.
2. Aseguradoras para planes de riesgo personalizados.
3. Instituciones de investigación médica.
4. Empresas de tecnología en bienestar y salud digital.

El proyecto tiene potencial para expandirse hacia otras enfermedades crónicas y convertirse en un pilar en la medicina preventiva.

### Propuesta de Valor

Un sistema de predicción de diabetes ofrecerá:

* **Prevención Temprana:** Identificación proactiva de pacientes en riesgo de desarrollar la enfermedad.
* **Optimización Clínica:** Uso eficiente de tiempo y recursos médicos.
* **Reducción de Costos:** Menor gasto en el manejo de complicaciones avanzadas.

## Alcance del Proyecto

### Incluye

* **Variables del Conjunto de Datos**:
  * **Datos Demográficos**:
    * Edad
    * Género
  * **Factores de Salud**:
    * Índice de Masa Corporal (IMC)
    * Niveles de glucosa en sangre
    * Nivel de HbA1c
  * **Historial Clínico**:
    * Hipertensión
    * Enfermedades cardíacas
    * Historial de tabaquismo
  * **Etiqueta**:
    * Presencia o ausencia de diabetes.

* **Fases del Proyecto**:
  * **Exploración de Datos**:
    * Análisis exploratorio de los datos
    * Análisis descriptivo de los datos
    * Análisis de la distribución de variables.
    * Identificación de correlaciones entre las variables.
  * **Preprocesamiento de Datos**:
    * Manejo de valores nulos
    * Manejo de valores faltantes
    * Codificación de variables categóricas.
    * Normalización/estandarización de variables continuas
  * **Construcción y Selección de Modelos**:
    * Selección de algoritmos de Machine Learning
    * Selección de hiperparametros para cada algoritmo
    * División en conjuntos de entrenamiento y prueba.
  * **Validación**:
    * Entrenamiento de los modelos
    * Comparación de modelos mediante métricas de desempeño
    * Evaluación de resultados
    * Selección del modelo final

* **Aplicaciones**:
  * Identificación temprana del riesgo de desarrollar diabetes en pacientes.
  * Análisis del impacto de factores demográficos y clínicos en el desarrollo de diabetes.
  * Uso como herramienta investigativa para profesionales médicos o educadores.

### Excluye

* **Datos No Proporcionados en el Conjunto de Datos:**
  * Variables genéticas.
  * Datos familiares detallados .
  * Análisis de imágenes.
  * Análisis de exámenes médicos
* **Diagnóstico Clínico:** El sistema es una herramienta predictiva, no un sustituto del diagnóstico médico.
* **Implementación Completa en Clínicas:** Integraciones con sistemas hospitalarios.

## Metodología

### Team Data Science Process (TDSP)

Es una metodología de ciencia de datos ágil e iterativa que se utiliza para ofrecer soluciones de análisis predictivo y aplicaciones de IA de manera eficiente. Ofrece un ciclo de vida enfocado en estructurar el desarrollo de proyectos de ciencia de datos exploratorios y proyectos de análisis de datos.

El ciclo de vida de TDSP consta de cinco etapas principales que se realizan de manera iterativa. Estas etapas son:

* **Comprensión Empresarial:** En esta atapa se busca especificar las variables clave que sirven como objetivos del modelo así como las métricas de los objetivos que determinan el éxito del proyecto.
* **Adquisición y Comprensión de Datos:** En esta etapa se busca generar un conjunto de datos limpio y de alta calidad que se relacione claramente con las variables objetivo. 
* **Modelado:** En esta etapa se busca crear un modelo de aprendizaje automático, con la mejor configuración de características (hiperparametros), capaz de predecir objetivo del proyecto con mayor precisión.
* **Despliegue:** En esta etapa se busca implementar el modelo con una canalización de datos en un entorno de producción para la aceptación del cliente final
* **Aceptación del Cliente:** En esta etapa se busca finalizar los entregables del proyecto. Se debe confirmar que el proceso de desarrollo, el modelo y su implementación en un entorno de producción satisfacen los objetivos del cliente
 
## Cronograma

| Etapa | Actividades | Duración Estimada |
| --- | --- | --- |
| Entendimiento del negocio y carga de datos | Construir el algoritmo que permita realizar la carga de los datos | Semana 18 - 24 Noviembre |
| | Definir el marco del proyecto | |
| | Crear un diccionario de datos | |
| Preprocesamiento, análisis exploratorio | Ejecutar un análisis exploratorio de los datos | Semana 25 - 1 Noviembre |
| | Realizar el preprocesamiento del conjunto de datos | |
| | Definir el conjunto de datos final | |
| | Generar un reporte con el resumen de los datos | |
| Modelamiento y extracción de características | Realizar la extracción de características | Semana 2 - 8 Diciembre |
| | Diseñar los modelos de clasificación | |
| | Generar un reporte con la línea base de los modelos | |
| | Seleccionar el modelo final | |
| Despliegue | Construir el algoritmo de despliegue | Semana 9 - 15 Diciembre |
| | Generar la documentación de despliegue | |
| | Generar la documentación de la infraestructura | |
| Evaluación y entrega final | Construir el algoritmo para la evaluación del modelo | Semana 16 – 22 Diciembre |
| | Realizar una interpretación de los resultados | |
| | Generar un reporte con las conclusiones del proyecto | |

## Equipo del Proyecto

* [JORGE LUIS RONCANCIO TURRIAGO](mailto:jroncanciot@unal.edu.co)
* [MANUEL FERNANDO NEIRA EMBUS](mailto:mfneirae@unal.edu.co)