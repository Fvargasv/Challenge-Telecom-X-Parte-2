# 📊 Telecom X – Parte 2: Predicción de Churn de Clientes

## 📌 Propósito del Análisis
Este proyecto tiene como objetivo principal **predecir la cancelación (churn) de clientes** de la compañía de telecomunicaciones **Telecom X**, utilizando información relevante sobre sus características demográficas, servicios contratados, patrones de uso y facturación.  
El objetivo es **identificar a clientes con alto riesgo de abandono** para implementar estrategias de retención más efectivas y enfocadas.

---

## 📂 Estructura del Proyecto

### 1. Preparación de los datos
### 2. Correlación y Selección de Variables
### 3. Modelado predictivo
### 4. Interpretación y Conclusiones

---
## 📥 Archivos y Descarga
- **Dataset:** `datos_telecomx_parte2.csv` disponible en el repositorio de GitHub.  
  Debe descargarse para ejecutar el análisis.
- **Notebook:** `Telecom_X_parte_2.ipynb` también disponible en el repositorio.  
  Se recomienda abrirlo en **Google Colab** para su ejecución, cargando previamente el archivo CSV.
---
## 🛠️ Preparación de los Datos

### 1. Clasificación de Variables
- **Categóricas:** género, tipo de contrato, tipo de servicio de internet, método de pago, etc.  
- **Numéricas:** `customer_tenure`, `Charges_Total`, `Charges_Dayly`, entre otras.

### 2. Codificación y Normalización
- **Codificación:** Variables categóricas transformadas con *One-Hot Encoding* mediante `make_column_transformer`.
- **Normalización:** Variables numéricas escaladas con **MinMaxScaler** para modelos como KNN.

### 3. Separación de Datos
- División del dataset en **70% entrenamiento** y **30% prueba** usando `train_test_split`.

### 4. Balanceo de Clases
- Se aplicó **SMOTE** para corregir el desbalance de la variable `Churn` (27% churn vs. 73% no churn).

---

## 📈 Justificación de Decisiones de Modelado
- **Selección de características:** *Permutation Importance* identificó las 9 variables más relevantes para el modelo KNN.
- **Optimización:** `GridSearchCV` se utilizó para maximizar el **recall**, priorizando la detección de clientes que efectivamente abandonarán.
- **Comparación de modelos:** Se evaluaron **DecisionTree** y **KNN** frente a un baseline (DummyClassifier), considerando métricas como accuracy, precisión, recall, F1-score y matrices de confusión.
- **Elección del modelo:** Se seleccionó **KNN optimizado para recall** por su mejor capacidad para detectar churn real.

---

## 🔍 Ejemplos de Gráficos e Insights (EDA)
1. **Distribución de Tenure según Churn:** El 75% de los clientes que se van tienen menos de 29 meses de permanencia.
2. **Boxplot de Charges_Dayly por Churn:** Los clientes que se van presentan cobros diarios más altos (25% pagan ≥ $1.9) que los que se quedan (25% pagan ≤ $0.8).
3. **Matriz de confusión:** El modelo KNN optimizado incrementa ligeramente los falsos positivos, pero reduce falsos negativos, mejorando la detección de churn real.

---

## Bibliotecas Usadas

import pandas as pd
from sklearn.compose import make_column_transformer
from sklearn.preprocessing import OneHotEncoder, MinMaxScaler
import seaborn as sns
from imblearn.over_sampling import SMOTE
import matplotlib.pyplot as plt
from sklearn.model_selection import train_test_split, KFold, cross_validate, GridSearchCV
from sklearn.dummy import DummyClassifier
from sklearn.tree import DecisionTreeClassifier
from sklearn.metrics import confusion_matrix, ConfusionMatrixDisplay
from sklearn.ensemble import RandomForestRegressor
from sklearn.neighbors import KNeighborsClassifier
from sklearn.inspection import permutation_importance
---
## Cargar los datos

1. Descargar datos_telecomx_parte2.csv desde el repositorio.
2. Abrir el notebook Telecom_X_parte_2.ipynb en Google Colab.
3. Subir el archivo CSV a Colab o montarlo desde Google Drive.

---

## Ejecutar el Notebook

1. Ejecutar todas las celdas en orden. El notebook incluye:
2. Preprocesamiento de datos.
3. Análisis exploratorio (EDA).
4. Entrenamiento y evaluación de modelos.
5. Selección y justificación del modelo final.
---

##📬 Contacto

Para consultas o sugerencias, abrir un issue en el repositorio o contactar a Felipe Vargas
