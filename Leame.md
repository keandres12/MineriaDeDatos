# 🎬 Minería de Datos: Predicción del Éxito Comercial y Mitigación de Riesgo en Hollywood

## 📋 Información del Proyecto
*   **Integrantes:** Kevin Castro
*   **Asignatura:** Mineria De Datos
*   **Dataset:** [Blockbuster Cinematic Archive (expensive_movie.csv)](https://www.kaggle.com/datasets/jaydeepahir18/hollywoods-most-expensive-blockbusters)
*   **Formato de Evaluación:** Encargo con Presentación (Defensa Oral Directa desde Google Colab)

## 📝 Descripción
Este proyecto implementa modelos avanzados de **Machine Learning** (Clasificación y Regresión) sobre un conjunto de datos de producciones cinematográficas de alto presupuesto. El objetivo principal es construir un sistema predictivo capaz de determinar si un proyecto alcanzará el "Éxito Comercial" antes de ser producido, actuando como una herramienta estratégica de gestión del riesgo financiero. El desarrollo resuelve problemas complejos detectados en la experiencia práctica, tales como el desbalanceo de clases, la imputación robusta de datos y la prevención de fuga de datos (*Data Leakage*).

## 🚀 Fases del Proyecto

### 1. Importación y Configuración Estructurada
*   Configuración del entorno en **Google Colab** y carga de librerías predictivas: `Scikit-Learn`, `Pandas`, `NumPy`, `Matplotlib` y `Seaborn`.
*   Carga y validación dimensional del archivo `expensive_movie.csv` para asegurar la correcta lectura del entorno de datos.

### 2. Justificación Técnica de Variables
*   **Selección por Naturaleza:** Clasificación del tipo de variables (cualitativas y cuantitativas) para determinar su compatibilidad algorítmica.
*   **Modelos de Clasificación:** Justificación del uso de variables de impacto social (`Popularity`, `Vote_Average`, `Vote_Count`) y temporales para estimar una etiqueta categórica binaria.
*   **Modelo de Regresión:** Justificación de variables puramente cuantitativas continuas para la proyección exacta de retornos monetarios.

### 3. Experiencia Práctica: Limpieza e Imputación Robusta
*   **Filtro Comercial de Calidad:** Identificación y remoción de registros con presupuestos (`Budget`) o ingresos (`Revenue`) en cero dólares, correspondientes a ruido de mercado o proyectos sin actividad financiera real.
*   **Tratamiento del Sesgo por Outliers:** Detección de valores nulos en la duración (`Runtime`) y métricas de votación. Solución aplicada mediante **imputación por la mediana matemática** en lugar de la media para evitar distorsiones por los grandes *blockbusters*.

### 4. Regla de Negocio e Ingeniería de Variables
*   **Umbral Financiero de Hollywood:** Creación de la variable objetivo binaria `Exito_Comercial`. Se aplica la regla internacional de distribución que dicta que una película es rentable solo si recauda al menos 2.5 veces su presupuesto de producción ($ROI \ge 2.5$).
*   **Procesamiento Cualitativo:** Extracción del género principal (`Main_Genre`) y simplificación de idiomas (`Language_Group`) mediante codificación de categorías para optimizar la densidad de la matriz de datos.

### 5. Rigurosidad Metodológica y Prevención de Trampas
*   **Control de Data Leakage:** Exclusión explícita de las columnas de retornos financieros (`Revenue` y `ROI`) de la matriz de entrenamiento $X$. Esto previene que los clasificadores memoricen la respuesta de forma tramposa.
*   **Estrategia de Partición:** Transformación mediante *One-Hot Encoding* y división del set de datos en 80% Entrenamiento y 20% Prueba de forma estrictamente **estratificada** para mantener las proporciones reales del mercado.

### 6. Experimentación Clasificatoria y Criterio de Negocio
*   **Tratamiento del Desbalanceo de Clases:** Implementación de penalizaciones por pesos (`class_weight='balanced'`) para corregir la tendencia del algoritmo a predecir únicamente la clase mayoritaria (fracasos).
*   **Torneo de Modelos:** Evaluación comparativa entre un *Árbol de Decisión Base*, un *Árbol Calibrado* y un **Random Forest Avanzado** (Ensamble de 100 estimadores en paralelo).
*   **Optimización de Métricas:** Enfoque prioritario en la métrica de **Precisión (Precision)** para reducir los *Falsos Positivos*, dado que avalar un proyecto multimillonario que resultará en fracaso representa un riesgo de quiebra corporativa.

### 7. Actividad Opcional: Puntaje Adicional (Regresión Lineal)
*   **Modelamiento Continuo:** Implementación de un modelo complementario de **Regresión Lineal** utilizando las variables cuantitativas continuas `Budget` (como predictora) y `Revenue` (como objetivo).
*   **Evaluación y Gráfica:** Análisis del coeficiente de determinación ($R^2$), error absoluto medio (MAE) y despliegue visual de la línea de ajuste para evaluar la correlación matemática directa entre el capital invertido y la recaudación final de taquilla.

## 🛠️ Tecnologías Utilizadas
*   **Python:** Lenguaje y motor principal de ejecución.
*   **Pandas & NumPy:** Ingeniería de variables, manipulación de matrices y limpieza estadística.
*   **Scikit-learn:** Construcción, calibración, partición y evaluación métrica de los modelos predictivos (`DecisionTreeClassifier`, `RandomForestClassifier`, `LinearRegression`).
*   **Matplotlib & Seaborn:** Generación de gráficos analíticos de dispersión y tendencias visuales para la defensa en clases.