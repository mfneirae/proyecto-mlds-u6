# Project Charter - Entendimiento del Negocio

## Nombre del Proyecto

Implementación Ágil de un Sistema de Machine Learning para la Predicción de Diabetes.

## Objetivo del Proyecto

Desarrollar e implementar un sistema de machine learning que permita predecir el riesgo de diabetes en pacientes a partir de datos médicos y demográficos, con el propósito de apoyar a profesionales de la salud en la toma de decisiones clínicas y la identificación temprana de casos de riesgo.

### Objetivos Específicos

* **Análisis de Datos:** Explorar y procesar el dataset para entender las relaciones entre las variables disponibles (edad, género, IMC, hipertensión, etc.) y el estado de diabetes.
* **Construcción del Modelo:** Entrenar y evaluar modelos de machine learning utilizando métricas de desempeño relevantes como precisión, sensibilidad y especificidad.
* **Validación y Optimización:** Implementar técnicas de validación cruzada y ajustar hiperparámetros para maximizar el rendimiento del modelo.
* **Despliegue del Sistema:** Crear un sistema accesible (por ejemplo, una API o una interfaz web) para que el modelo pueda ser utilizado por profesionales de la salud.
* **Documentación y Capacitación:** Proveer documentación clara y realizar capacitaciones para garantizar la adopción efectiva del sistema.

## Transfondo del Negocio

### Contexto

La diabetes es una de las enfermedades crónicas más comunes, afectando a millones de personas a nivel global. Su diagnóstico tardío y falta de herramientas predictivas generan altos costos médicos y reducen la calidad de vida de los pacientes. Los sistemas de salud necesitan soluciones tecnológicas para identificar riesgos tempranos y prevenir complicaciones asociadas.

### Problema

1. **Diagnóstico tardío:** Frecuente detección en etapas avanzadas.
2. **Recursos limitados:** Insuficiente personal médico para análisis masivos.
3. **Fragmentación de datos:** Falta de integración y análisis predictivo efectivo.

### Oportunidad

El uso de machine learning permite construir sistemas predictivos que:

* Ayudan a profesionales médicos a evaluar riesgos en grandes poblaciones.
* Reducen costos asociados con complicaciones de diabetes.
* Proveen herramientas escalables y accesibles para diversas instituciones.

### Propuesta de Valor

Un sistema de predicción de diabetes ofrecerá:

* **Prevención temprana:** Identificación proactiva de casos en riesgo.
* **Optimización clínica:** Uso eficiente de tiempo y recursos médicos.
* **Reducción de costos:** Menor gasto en el manejo de complicaciones avanzadas.

### Mercado Objetivo

1. Sistemas de salud públicos y privados.
2. Aseguradoras para planes de riesgo personalizados.
3. Instituciones de investigación médica.
4. Empresas de tecnología en bienestar y salud digital.

El proyecto tiene potencial para expandirse hacia otras enfermedades crónicas y convertirse en un pilar en la medicina preventiva.

## Alcance del Proyecto

### Incluye

1. **Variables del Dataset**:
   * **Datos demográficos**:
     * Edad
     * Género
   * **Factores de salud**:
     * Índice de Masa Corporal (IMC)
     * Niveles de glucosa en sangre
     * Presión arterial
   * **Historial clínico**:
     * Enfermedades cardíacas
     * Historial de tabaquismo
   * **Etiqueta**:
     * Presencia o ausencia de diabetes tipo 2.tabaquismo.
2. **Fases del Proyecto**:
   * **Exploración de Datos**:
     * Análisis de la distribución de variables.
     * Identificación de correlaciones entre las variables y el riesgo de diabetes.
   * **Preprocesamiento de Datos**:
     * Manejo de valores nulos.
     * Codificación de variables categóricas como género y tabaquismo.
     * Normalización/estandarización de variables continuas (e.g., glucosa, IMC).
   * **Construcción y Selección de Modelos**:
     * Evaluación de algoritmos como:
       * Regresión logística
       * Random Forest
     * Comparación de modelos mediante métricas clave:
       * AUC-ROC
       * F1-score
       * Precisión
   * **Validación**:
     * División en conjuntos de entrenamiento y prueba.

3. **Aplicaciones**:
   * Identificación temprana del riesgo de diabetes en pacientes.
   * Análisis del impacto de factores demográficos y clínicos en el desarrollo de diabetes.
   * Uso como herramienta investigativa para profesionales médicos o educadores.

### Excluye

* **Datos No Proporcionados por el Dataset:**
  * Variables genéticas, datos familiares detallados o análisis de imágenes.
* **Diagnóstico Clínico:**
  * El sistema es una herramienta predictiva, no un sustituto del diagnóstico médico.
* **Implementación Completa en Clínicas:**
  * Integraciones con sistemas hospitalarios.

## Metodología

### #TODO

[Descripción breve de la metodología que se utilizará para llevar a cabo el proyecto]

## Cronograma

### #TODO

| Etapa | Duración Estimada | Fechas |
|------|---------|-------|
| Entendimiento del negocio y carga de datos | 2 semanas | del 1 de mayo al 15 de mayo |
| Preprocesamiento, análisis exploratorio | 4 semanas | del 16 de mayo al 15 de junio |
| Modelamiento y extracción de características | 4 semanas | del 16 de junio al 15 de julio |
| Despliegue | 2 semanas | del 16 de julio al 31 de julio |
| Evaluación y entrega final | 3 semanas | del 1 de agosto al 21 de agosto |

Hay que tener en cuenta que estas fechas son de ejemplo, estas deben ajustarse de acuerdo al proyecto.

## Equipo del Proyecto

* [Jorge Luis Roncancio Turriago](mailto:jroncanciot@unal.edu.co)
* [Manuel Fernando Neira Embus](mailto:mfneirae@unal.edu.co)

## Presupuesto

[Descripción del presupuesto asignado al proyecto]
