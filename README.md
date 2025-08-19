# Análisis de Predicción de Churn de Clientes

## Propósito del Análisis

El objetivo principal de este proyecto es identificar los factores que influyen en la cancelación de clientes (churn) y construir un modelo predictivo para anticipar qué clientes tienen mayor probabilidad de cancelar su servicio. Esto permitirá a la empresa implementar estrategias de retención dirigidas y mejorar la satisfacción del cliente.

## Estructura del Proyecto

El proyecto se organiza de la siguiente manera:

- `TelecomX2.ipynb`: Cuaderno principal que contiene todo el código para el análisis, desde la carga de datos hasta la modelización y evaluación.
- `datos.csv`: Archivo CSV con los datos brutos utilizados para el análisis.

## Proceso de Preparación de Datos

1.  **Carga de Datos**: Los datos se cargaron desde el archivo `datos.csv` utilizando la biblioteca pandas.
2.  **Clasificación de Variables**: Las variables se clasificaron en categóricas (como `gender`, `Contract`, `PaymentMethod`) y numéricas (como `tenure`, `Charges.Monthly`, `Charges.Total`).
3.  **Limpieza y Transformación**: Se eliminaron columnas irrelevantes (`customerID`, `Charges.Total`). Se realizó la codificación de variables categóricas: `gender` se mapeó a 0 y 1, y otras variables categóricas se transformaron utilizando One-Hot Encoding.
4.  **Balanceo de Clases**: Dado el desbalance en la variable objetivo (`Churn`), se aplicó SMOTE para balancear las clases en el conjunto de entrenamiento.
5.  **Separación de Datos**: Los datos se dividieron en conjuntos de entrenamiento y prueba (80% y 20% respectivamente) para evaluar el rendimiento de los modelos de forma imparcial. Se utilizó estratificación para mantener la proporción de la variable objetivo en ambos conjuntos.

## Modelización

Se exploraron dos modelos predictivos:

-   **K-Nearest Neighbors (KNN)**: Se aplicó normalización a las variables numéricas antes de entrenar el modelo KNN.
-   **Árbol de Decisión**: Este modelo no requiere normalización.

Se justificó la elección de estos modelos por su interpretabilidad (especialmente el Árbol de Decisión) y su capacidad para manejar datos con características tanto numéricas como categóricas (después de la codificación).

## Análisis Exploratorio de Datos (EDA) e Insights

Durante el EDA, se obtuvieron insights importantes, como:

-   La proporción de clientes que cancelaron (`Churn`) fue aproximadamente del 26.5%.
-   Visualizaciones como el boxplot de `Contract` vs `Churn` y `TotalCharges` vs `Churn` mostraron que los clientes con contratos mes a mes y con altos cargos mensuales tienen una mayor tendencia a cancelar.
-   El análisis de importancia de las variables en el Árbol de Decisión identificó a `tenure`, `PaymentMethod_Electronic check`, `Cuentas_Diarias`, `Charges.Monthly`, y `InternetService_Fiber optic` como las variables más relevantes para la predicción de churn.
