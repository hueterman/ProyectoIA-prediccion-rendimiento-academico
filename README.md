# Predicción del rendimiento académico con Machine Learning

TFM — Especialización en Inteligencia Artificial · Pedro Huete Toral

## Descripción

Proyecto que predice la calificación final (`Grade`) de estudiantes a partir de un dataset real de 5.000 registros, combinando variables académicas (asistencia, notas, participación, horas de estudio...) y socio-demográficas (departamento, nivel educativo de los padres, nivel de ingresos familiares...).

Dataset original: [Students Grading Dataset (Kaggle)](https://www.kaggle.com/datasets/mahmoudelhemaly/students-grading-dataset)

## Objetivos

- Clasificación de la calificación del estudiante.
- Análisis de correlación entre variables y la calificación.
- Limpieza, conversión y creación de variables.
- Comparación de distintos modelos de Machine Learning y redes neuronales.

## Proceso y resultados

1. **Análisis exploratorio y preprocesamiento**: nulos, duplicados, atípicos y correlaciones; variables categóricas convertidas a numéricas.
2. **Modelos clásicos** (regresión lineal, regresión logística, SVM, árboles de decisión, bosques aleatorios, Gradient Boosting) sobre las 5 clases originales (A-F): 25%-32% de precisión.
3. **Redes neuronales** (MLP, red simple, DNN): mejora ligera, 35%-37%.
4. **Feedback del profesor**: `Grade` es una variable ordinal, las clases están desbalanceadas y hay ruido inherente en los datos.
5. **Reducción a 3 clases** (Bajo / Medio / Alto) + Random Forest con `class_weight='balanced'`: 61% de precisión.
6. **SMOTE (sobremuestreo)** + Random Forest: mejor resultado del proyecto, ~88% de precisión sobre el conjunto de entrenamiento reequilibrado. Una DNN con SMOTE, evaluada en test real, se quedó en 60%.

El notebook completo (`ProyectoIA.ipynb`) incluye el análisis, el código y las conclusiones finales de todo el proceso.

## Estructura del repositorio

- `ProyectoIA.ipynb` — notebook completo del proyecto (análisis, modelos y conclusiones).
- `TFM_LinkedIn_Slides.pptx` — resumen visual del proyecto en formato de slides.

## Limitaciones y líneas futuras

- La evaluación final de Random Forest + SMOTE se realizó sobre el conjunto de entrenamiento reequilibrado, no sobre el conjunto de test independiente; queda pendiente validarla sobre datos no vistos.
- Quedan por explorar: clasificador ordinal, feature engineering adicional, búsqueda de hiperparámetros y fijar semillas aleatorias para reproducibilidad.
