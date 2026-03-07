# intrusion-detection-eda

Analisis exploratorio y modelado base para deteccion de intrusiones en trafico de red, desarrollado como trabajo practico academico de maestria.

## Objetivo

Construir un flujo reproducible de Cybersecurity Analytics para:

- inspeccionar y limpiar datos de trafico de red;
- identificar patrones entre trafico normal y malicioso;
- generar visualizaciones interpretables;
- entrenar un modelo baseline de clasificacion multiclase.

## Dataset

Archivos utilizados:

- `data/train_data.csv` (o `data/Train_data.csv` segun el entorno local)
- `data/test_data.csv`

Variable objetivo:

- `xAttack` con clases: `normal`, `dos`, `probe`, `r2l`, `u2r`

Tamano despues de limpieza:

- train: `125,941 x 42`
- test: `9,999 x 42`

Notas de calidad:

- sin valores nulos;
- 32 duplicados removidos en train;
- columna tecnica `Unnamed: 0` removida de test.

## Notebook principal

- `notebooks/01_intrusion_detection_eda.ipynb`

El notebook contiene las secciones completas del trabajo:

1. Title
2. Introduction
3. Dataset Description
4. Data Loading
5. Initial Data Inspection
6. Data Quality Analysis
7. Data Cleaning
8. Exploratory Data Analysis (EDA)
9. Data Visualization
10. Correlation Analysis
11. Cybersecurity Insights
12. Machine Learning (baseline)
13. Conclusions

## Principales hallazgos

- El dataset presenta desbalance marcado: `normal` y `dos` concentran la mayoria de observaciones; `u2r` y `r2l` son clases minoritarias.
- Variables de volumen (`src_bytes`, `dst_bytes`), conteo (`count`, `srv_count`) y tasas de error/consistencia muestran capacidad discriminante para deteccion.
- El baseline de `RandomForestClassifier` logra resultados altos en validacion interna, pero menor desempeno en test externo, indicando posible cambio de distribucion y mayor dificultad en generalizacion multiclase.

Metricas del baseline (split de validacion):

- accuracy: `0.9990`
- precision macro: `0.9710`
- recall macro: `0.8857`
- f1 macro: `0.9165`
- f1 weighted: `0.9990`

Metricas en test externo:

- accuracy: `0.7378`
- precision macro: `0.8866`
- recall macro: `0.4701`
- f1 macro: `0.4723`
- f1 weighted: `0.6905`

## Estructura del repositorio

```text
intrusion-detection-eda/
├─ data/
│  ├─ train_data.csv (o Train_data.csv)
│  └─ test_data.csv
├─ notebooks/
│  └─ 01_intrusion_detection_eda.ipynb
├─ requirements.txt
└─ README.md
```

## Como ejecutar

1. Crear y activar entorno virtual (opcional, recomendado).
2. Instalar dependencias:

```bash
pip install -r requirements.txt
```

3. Abrir el notebook:

```bash
jupyter notebook notebooks/01_intrusion_detection_eda.ipynb
```

4. Ejecutar todas las celdas en orden (`Run All`) para reproducir resultados.

## Dependencias

Ver `requirements.txt`. Librerias principales:

- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn
- jupyter
