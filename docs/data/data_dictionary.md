# Diccionario de datos

## Base de datos `diabetes_prediction_dataset.csv`

Este conjunto de datos contiene información relacionada con la salud de los pacientes, como la edad, el sexo, los antecedentes de tabaquismo, el IMC y el nivel de HbA1c, con el objetivo de predecir la diabetes.

| Variable | Descripción | Tipo de dato | Rango/Valores posibles | Fuente de datos |
|---|---|---|---|---|
| gender | Género del paciente (masculino, femenino u otro) | Categórico | Femenino, Masculino, Otro | diabetes_prediction_dataset (1).csv |
| age | Edad del paciente en años | Numérico | 0-100 | diabetes_prediction_dataset (1).csv |
| hypertension | Indica si el paciente tiene hipertensión (0: no, 1: sí) | Categórico | 0, 1 | diabetes_prediction_dataset (1).csv |
| heart_disease | Indica si el paciente tiene una enfermedad cardíaca (0: no, 1: sí) | Categórico | 0, 1 | diabetes_prediction_dataset (1).csv |
| smoking_history | Los antecedentes de tabaquismo del paciente, que incluyen categorías como nunca fumador, fumador actual, exfumador y otras. | Categórico | never, No Info, current, former, ever, not current | diabetes_prediction_dataset (1).csv |
| bmi | Índice de masa corporal del paciente, que es una medida de la grasa corporal según la estatura y el peso | Numérico | 10.01-71.74 | diabetes_prediction_dataset (1).csv |
| HbA1c_level | Nivel de HbA1c del paciente, que es una medida del nivel promedio de glucosa en sangre durante los últimos 2 o 3 meses | Numérico | 3.5-9.5 | diabetes_prediction_dataset (1).csv |
| blood_glucose_level | Nivel de glucosa en sangre del paciente en el momento de la prueba, que es una medida de la cantidad de glucosa en sangre | Numérico | 80-300 | diabetes_prediction_dataset (1).csv |
| diabetes | Indica si el paciente tiene diabetes (0: no, 1: sí) | Categórico | 0, 1 | diabetes_prediction_dataset (1).csv |

- **Variable**: nombre de la variable.
- **Descripción**: breve descripción de la variable.
- **Tipo de dato**: tipo de dato que contiene la variable.
- **Rango/Valores posibles**: rango o valores que puede tomar la variable.
- **Fuente de datos**: fuente de los datos de la variable.
