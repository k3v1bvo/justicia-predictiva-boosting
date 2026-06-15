# 📊 Predicción de Duración de Casos Judiciales Cerrados en Bolivia

## 🎓 Información del Proyecto

| Campo | Detalle |
|-------|---------|
| **Materia** | Tecnologías Emergentes (TI26) |
| **Autores** | Vergara & Patiño |
| **Dataset** | Casos Cerrados del Ministerio Público de Bolivia |
| **Objetivo** | Predecir la duración (en días) de casos judiciales cerrados |

## 📁 Estructura del Repositorio

```
repositorio-TI26-[Vergara&Patiño]/
├── data/
│   ├── raw/                                      # Datos crudos originales
│   │   └── CASOS_CERRADOS_publico_1.csv
│   └── processed/                                # Datos procesados (generados por notebook 02)
├── notebooks/
│   ├── 01_EDA.ipynb                              # Análisis Exploratorio de Datos
│   ├── 02_preprocessing.ipynb                    # Preprocesamiento y limpieza
│   ├── 03_model_main.ipynb                       # Modelos base (Reg. Lineal + Random Forest)
│   └── 04_model_comparison.ipynb                 # Modelos Boosting (XGBoost, Gradient Boost, AdaBoost)
├── notebooks_colab/                              # Versiones adaptadas para Google Colab
│   ├── 01_EDA_colab.ipynb
│   ├── 02_preprocessing_colab.ipynb
│   ├── 03_model_main_colab.ipynb
│   └── 04_model_comparison_colab.ipynb
├── docs/
│   ├── doc.pdf                                   # Informe final del proyecto
│   └── prese.pdf                                 # Presentación del proyecto
├── images/                                       # Gráficos generados por los notebooks
│   ├── edades_distribucion.png
│   ├── duracion_meses.png
│   ├── duracion_departamento.png
│   ├── curva_roc_boosting.png
│   └── matrices_confusion.png
├── results/
│   ├── resultados_modelos_base.csv               # Métricas Fase 1 (Regresión)
│   └── resultados_clasificacion_boosting.csv     # Métricas Fase 2 (Clasificación)
├── README.md
├── requirements.txt
└── .gitignore
```

## 🔬 Metodología

### 1. Análisis Exploratorio (EDA)
- Distribución de edades de víctimas y denunciados
- Duración promedio de casos por mes y por departamento
- Análisis de correlaciones entre variables

### 2. Preprocesamiento
- Limpieza de fechas con formato válido (`dd-MM-yyyy HH:mm:ss`)
- Cálculo de la variable objetivo: `duracion_dias = fecha_cierre - fecha_denuncia`
- Codificación de variables categóricas (`delito`, `hecho_departamento`)
- Imputación de valores nulos

### 3. Fases del Proyecto y Modelos Implementados

**Fase 1: Estudio Previo (Regresión)**
Predicción de la duración exacta en días.
- **Modelos:** Regresión Lineal, Random Forest Regressor
- **Métricas:** RMSE, MAE, R²

**Fase 2: Estudio Principal — Clasificación con Boosting**
Predicción de si un caso será de larga duración (> 1 año) o corto.
- **Modelos:** Gradient Boosting, XGBoost, AdaBoost
- **Métricas:** Accuracy, F1-Score, AUC-ROC, Matriz de Confusión

### 4. Validación
- Split 70/30 con semilla fija para garantizar reproducibilidad

## 📊 Resultados Obtenidos

### Fase 1 — Regresión

| Modelo | RMSE | MAE | R² |
|--------|------|-----|----|
| Regresión Lineal | 663.24 | 355.44 | 0.088 |
| Random Forest | 496.09 | 246.29 | 0.489 |

### Fase 2 — Clasificación Boosting

| Modelo | Accuracy | F1-Score | AUC-ROC |
|--------|----------|----------|---------|
| Gradient Boost | 89.31% | 0.709 | 0.953 |
| **XGBoost** | **89.96%** | **0.740** | **0.959** |
| AdaBoost | 87.18% | 0.626 | 0.931 |

> 🏆 **XGBoost** obtuvo el mejor rendimiento con 89.96% de accuracy y AUC-ROC de 0.959.

## 🛠️ Tecnologías Utilizadas

- **Apache Spark (PySpark)** – Procesamiento distribuido de datos
- **scikit-learn** – Modelos de Machine Learning
- **XGBoost** – Gradient Boosting optimizado
- **Matplotlib / Seaborn** – Visualización de datos
- **Google Colab** – Entorno de ejecución en la nube

## 🚀 Cómo Ejecutar

### Entorno Local (Jupyter)

1. Instalar dependencias:
   ```bash
   pip install -r requirements.txt
   ```
2. Colocar el archivo `CASOS_CERRADOS_publico_1.csv` en `data/raw/`
3. Ejecutar los notebooks en orden:
   - `01_EDA.ipynb` → EDA y gráficos
   - `02_preprocessing.ipynb` → Datos procesados
   - `03_model_main.ipynb` → Modelos base
   - `04_model_comparison.ipynb` → Modelos Boosting

### Google Colab
Usar los notebooks de la carpeta `notebooks_colab/` directamente.

## 📦 Dependencias

```bash
pip install pyspark xgboost scikit-learn matplotlib seaborn pandas numpy
```

## 📝 Licencia

Proyecto académico — Universidad de Bolivia — 2025
