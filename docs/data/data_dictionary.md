# Diccionario de Datos

## Conjunto de Datos `diabetes_prediction_dataset.csv`

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
| **diabetes** | Indica si el paciente tiene diabetes | Categórico (bool) | 0, 1 (0: No, 1: Sí) |