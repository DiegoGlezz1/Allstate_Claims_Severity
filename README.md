# Predicción de la Severidad de Siniestros (Allstate)

Este proyecto es parte de mi portafolio de Ciencia de Datos. El objetivo es construir un modelo de machine learning para predecir el costo de las reclamaciones de seguros de auto.

---

### 1. Planteamiento del Problema

El objetivo es predecir la severidad de un siniestro basándose en las características de la póliza y del incidente. Una predicción precisa ayuda a la aseguradora a gestionar sus reservas financieras de manera más eficiente.

---

### 2. El Dataset

* **Fuente:** [Competencia de Kaggle "Allstate Claims Severity"](https://www.kaggle.com/c/allstate-claims-severity/data)
* **Descripción:** El dataset contiene 130 características anónimas (116 categóricas y 14 continuas) por cada ID de siniestro.
* **Variable Objetivo:** `loss`.

---

### 3. Metodología y Hallazgos Clave

Mi proceso de análisis y modelado fue el siguiente:

* **Análisis Exploratorio:** Identifiqué un fuerte **sesgo positivo** en la variable objetivo `loss`.
* **Preprocesamiento:**
    * Apliqué una **transformación logarítmica** a la variable `loss` para normalizar su distribución ya que mostraba una tendencia logaritmica.
    * Convertí las 116 variables categóricas usando **One-Hot Encoding**.
* **Modelado:**
    * Dividí los datos en conjuntos de entrenamiento y prueba (80/20).
    * Entrené un modelo **XGBoost Regressor**, que es muy funcional para este dataset y maneja bien la alta dimensionalidad del One-Hot Encoding.
* **Evaluación:**
    * La métrica de evaluación fue el **Error Absoluto Medio (MAE)**.
    * Revertí la transformación logarítmica  en las predicciones antes de calcular el error.

---

### 4. Resultados

El modelo final de XGBoost (con 500 estimadores) alcanzó un **MAE de 1140.99**.

Este es un resultado muy sólido, lo que indica que el modelo es capaz de predecir el costo del siniestro con un error promedio de ~$1,141.

---

### 5. Herramientas Utilizadas

* **Python**
* **Pandas** y **NumPy** para la manipulación y transformación de datos.
* **Seaborn** y **Matplotlib** para la visualización.
* **Scikit-learn** para el preprocesamiento (`ColumnTransformer`, `OneHotEncoder`, `train_test_split`).
* **XGBoost** para el modelado de regresión.
