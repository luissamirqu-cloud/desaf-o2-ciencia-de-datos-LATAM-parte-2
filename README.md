# Telecom X: Modelado Predictivo de Churn (Fase 2)

Este repositorio contiene la segunda etapa del proyecto **Telecom X**, enfocada en la implementación de algoritmos de aprendizaje supervisado para la predicción de fuga de clientes. El flujo de trabajo abarca desde el preprocesamiento avanzado hasta la interpretación de modelos de "caja negra".

## Propósito del Análisis

El objetivo principal es construir un sistema de clasificación que identifique patrones de abandono en la base de clientes de la operadora. Se abordan desafíos críticos de datos reales como:

* **Desbalanceo de Clases:** Implementación de técnicas sintéticas para equilibrar la variable objetivo.
* **Tratamiento de Outliers:** Uso de escaladores robustos para mitigar el impacto de valores extremos en variables financieras.
* **Interpretabilidad:** Aplicación de métodos de permutación para entender los factores que más influyen en el modelo.

## Estructura del Proyecto

El notebook `Analisis_Churn_TelecomX_v2_Luis.ipynb` está organizado en los siguientes módulos técnicos:

1.  **Ingesta de Datos:** Carga y validación del dataset procesado en la fase anterior.
2.  **Ingeniería de Características:** * **Ordinal Encoding:** Transformación de variables categóricas preservando la dimensionalidad del dataset.
    * **Selección via Chi-Cuadrado:** Identificación de la relevancia estadística de cada variable respecto a la cancelación.
3.  **Pipeline de Preprocesamiento:**
    * **SMOTETomek:** Combinación de sobremuestreo (SMOTE) y limpieza de enlaces de Tomek para reducir el ruido en las fronteras de decisión.
    * **RobustScaler:** Normalización de columnas numéricas (Meses de Contrato, Cobros, etc.) basándose en percentiles.
4.  **Modelado y Evaluación:**
    * Entrenamiento de **Support Vector Machine (SVM)** con kernel RBF.
    * Entrenamiento de **K-Nearest Neighbors (KNN)** con métrica Manhattan.
5.  **Interpretación:** Análisis de importancia por permutación para ambos modelos.

## Insights y Métricas Clave

### Relevancia de Variables
Mediante la prueba de **Chi-Cuadrado**, se determinó que los factores contractuales y los cargos totales son los predictores con mayor peso estadístico antes del entrenamiento.

### Desempeño de los Modelos
El análisis incluye reportes detallados de:
* **Precisión y Recall:** Balance entre la detección de evasores y la reducción de falsas alarmas.
* **Curva ROC/AUC:** Medición de la capacidad de separación de clases de los modelos SVM y KNN.

### Hallazgos Estratégicos
* **Factores de Riesgo:** El modelo identifica que los cargos mensuales elevados y ciertos métodos de pago aumentan significativamente el riesgo de churn.
* **Factores de Retención:** La antigüedad del contrato (tenure) actúa como el principal estabilizador del cliente.

## Instrucciones de Ejecución

### Requisitos Técnicos
Es necesario un entorno con Python 3.x y las siguientes librerías:
* `pandas`, `numpy`, `matplotlib`, `seaborn`
* `scikit-learn`
* `imblearn` (Imbalanced-learn)

### Pasos para Reproducción
1.  Clonar este repositorio o descargar el archivo `.ipynb`.
2.  Ejecutar el notebook en un entorno compatible (Jupyter o Google Colab).
3.  Al ser solicitado, cargar el archivo fuente `telecom_x_limpio.csv`.
4.  Seguir la ejecución secuencial de las celdas para generar los reportes y visualizaciones.

---
**Nota:** Este proyecto forma parte de un análisis integral de Ciencia de Datos para el sector de Telecom
