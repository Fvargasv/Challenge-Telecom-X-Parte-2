# Challenge-Telecom-X-Parte-2
Desafío Challenge X Alura Latam Parte 2
# 📊 Telecom X – Parte 2: Predicción de Churn de Clientes

## 📌 Propósito del Análisis
Este proyecto tiene como objetivo principal **predecir la cancelación (churn) de clientes** de la compañía de telecomunicaciones **Telecom X**, utilizando información relevante sobre sus características demográficas, servicios contratados, patrones de uso y facturación.  
El fin último es **identificar a clientes con alto riesgo de abandono** para implementar estrategias de retención más efectivas y enfocadas.

---

## 📂 Estructura del Proyecto
Telecom_X_Parte_2/
│
├── data/
│ ├── datos_tratados.csv # Dataset final después de limpieza y preprocesamiento
│
├── notebooks/
│ ├── TelecomX_Churn_Parte2.ipynb # Cuaderno principal de análisis y modelado
│
├── visualizations/
│ ├── boxplot_tenure_churn.png
│ ├── scatter_tenure_charges.png
│ ├── matriz_confusion_knn.png
│ ├── matriz_confusion_decisiontree.png
│
├── README.md # Este archivo

yaml
Copiar
Editar

---

## 🛠️ Preparación de los Datos

### 1. Clasificación de Variables
- **Categóricas:** Variables como género, tipo de contrato, tipo de servicio de internet, método de pago, etc.  
- **Numéricas:** Tenure (meses de permanencia), Charges_Total (cargos totales), Charges_Dayly (cargos diarios), entre otras.

### 2. Codificación y Normalización
- **Codificación:** Variables categóricas transformadas con *One-Hot Encoding*.  
- **Normalización:** Variables numéricas normalizadas para modelos sensibles a la escala como KNN.

### 3. Separación de Datos
- **Entrenamiento y prueba:** División del dataset en 80% entrenamiento y 20% prueba para validar la capacidad de generalización de los modelos.

---

## 📈 Justificación de Decisiones de Modelado
- **Selección de características:** Se realizó un análisis de *Permutation Importance* para el modelo KNN, conservando las 9 variables con mayor relevancia.
- **Balanceo de clases:** Dado que solo el 27% de clientes corresponde a casos de churn, se aplicó **SMOTE** para balancear las clases y mejorar la detección de la clase minoritaria.
- **Optimización de hiperparámetros:** Para KNN se utilizó `GridSearchCV` con optimización del **recall**, priorizando la detección de clientes que efectivamente se irán.
- **Comparación de modelos:** Se evaluaron KNN y DecisionTree frente a un modelo baseline, analizando métricas como accuracy, precisión, recall, F1-score y matrices de confusión.

---

## 🔍 Ejemplos de Gráficos e Insights (EDA)
1. **Distribución de Tenure según Churn:** El 75% de los clientes que se van tienen menos de 29 meses de permanencia.
2. **Boxplot de Charges_Dayly por Churn:** Los clientes que se van presentan cobros diarios más altos (25% pagan ≥ $1.9) que los que se quedan (25% pagan ≤ $0.8).
3. **Matriz de confusión:** El modelo KNN optimizado incrementa ligeramente los falsos positivos, pero reduce falsos negativos, mejorando la detección de churn real.

---

## 🚀 Instrucciones de Ejecución

### 1. Requisitos Previos
Instalar las bibliotecas necesarias:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn imbalanced-learn
2. Cargar los Datos
Colocar el archivo datos_tratados.csv en la carpeta data/.

3. Ejecutar el Cuaderno
Abrir el archivo TelecomX_Churn_Parte2.ipynb y ejecutar las celdas en orden.
El cuaderno contiene:

Limpieza y preprocesamiento de datos.

Análisis exploratorio (EDA).

Entrenamiento y evaluación de modelos (DecisionTree y KNN).

Selección del modelo final (KNN optimizado para recall).

📬 Contacto
Si tienes preguntas o sugerencias sobre este proyecto, no dudes en abrir un issue o enviar un mensaje.
