# Stroke Classification Project

Proyecto academico de clasificacion supervisada sobre el `Stroke Prediction Dataset` de Kaggle. El repositorio integra dos entregables:

- un notebook reproducible para EDA, preprocesamiento, entrenamiento y comparacion de modelos;
- un articulo en formato IEEE con resultados, figuras y discusion metodologica.

## Estructura del repositorio

```text
.
├── .gitignore
├── README.md
├── requirements.txt
├── data/
│   └── .gitkeep
├── figures/
│   ├── cm_baseline_models.png
│   ├── cm_final_models.png
│   ├── eda_categorical.png
│   └── eda_continuous.png
├── notebooks/
│   └── actividad_clasificacion_stroke.ipynb
├── paper/
│   ├── articulo_stroke_ieee.tex
│   └── articulo_stroke_ieee.pdf
└── results/
    └── .gitkeep
```

## Objetivo

Comparar regresion logistica y Naive Bayes para predecir `stroke` a partir de variables continuas y categoricas. El flujo incluye:

- analisis exploratorio de datos;
- preprocesamiento con imputacion, `OneHotEncoder` y `StandardScaler`;
- entrenamiento de modelos base;
- diagnostico del sesgo de la regresion logistica inicial;
- ajuste con `class_weight="balanced"` y seleccion de umbral;
- integracion de resultados en un manuscrito IEEE.

## Requisitos

- Python 3.11+
- MacTeX completo para compilar el articulo
- Dependencias Python listadas en `requirements.txt`

## Configuracion del entorno

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install --upgrade pip
pip install -r requirements.txt
```

Si el entorno no tiene acceso directo al dataset, el notebook permite:

- descargarlo con `kagglehub`;
- o definir una ruta local en `LOCAL_DATA_PATH`.

## Ejecucion del notebook

El notebook principal esta en:

- [notebooks/actividad_clasificacion_stroke.ipynb](notebooks/actividad_clasificacion_stroke.ipynb)

Al ejecutarlo de arriba hacia abajo:

- las figuras exportables se guardan en `figures/`;
- las tablas de resultados se guardan en `results/`.

Nota: el notebook detecta si se ejecuta desde `notebooks/` y exporta automaticamente hacia la raiz del proyecto.

## Compilacion del articulo IEEE

El archivo fuente del articulo esta en:

- [paper/articulo_stroke_ieee.tex](paper/articulo_stroke_ieee.tex)

Compilacion manual:

```bash
cd paper
latexmk -pdf articulo_stroke_ieee.tex
```

Limpieza de artefactos LaTeX:

```bash
cd paper
latexmk -c articulo_stroke_ieee.tex
```

## Contenido del articulo

El manuscrito ya incluye:

- resumen del dataset;
- resultados del experimento base;
- comparacion final entre modelos;
- figuras de EDA y matrices de confusion;
- discusion metodologica sobre desbalance de clases;
- conclusiones alineadas con los resultados del notebook.

## Datos

El dataset no se incluye en el repositorio por tratarse de un recurso externo de Kaggle. La carpeta `data/` queda reservada para futuras integraciones o archivos auxiliares pequenos; por ahora solo se conserva con `.gitkeep` para mantener la estructura del proyecto.

## Sugerencia de versionado

Se recomienda versionar:

- notebook fuente;
- figuras finales usadas en el articulo;
- manuscrito `.tex`;
- PDF final del articulo;
- tablas CSV finales si quieres trazabilidad numerica.

Y evitar versionar:

- artefactos de compilacion LaTeX;
- checkpoints de Jupyter;
- descargas crudas del dataset;
- archivos temporales del sistema.
