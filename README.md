# Retail Insights — Análisis exploratorio de ventas

Proyecto para realizar un análisis exploratorio (EDA) sobre el dataset "Sample - Superstore.csv" y extraer insights de ventas, rentabilidad y comportamiento de clientes.

## Contenido

- `data/raw/` — datos originales (ej. `Sample - Superstore.csv`).
- `data/staging/` — datos transformados intermedios.
- `data/curated/` — datos limpios listos para análisis.
- `notebooks/` — notebooks exploratorios (ej. `notebook.ipynb`).
- `main.py` — script principal (si aplica) para reproducir pasos.

## Requerimientos

Recomendado usar un entorno virtual con Python 3.9+ e instalar dependencias (pandas, numpy, matplotlib, seaborn, plotly, geopandas opcional). Puedes usar `pyproject.toml` o instalar manualmente:

```bash
# pip
python -m venv .venv
source .venv/bin/activate
pip install pandas numpy matplotlib seaborn ipikernel

# uv
uv sync --group dev
```

## Datos

El dataset principal está en `data/raw/Sample - Superstore.csv`. Antes de empezar, revisa la licencia del origen de los datos y evita exponer información sensible.

## Uso rápido

1. Coloca el CSV en `data/raw/` si no está.
2. Abre `notebooks/notebook.ipynb` para reproducir el análisis.

Ejemplo mínimo en Python para cargar los datos:

```python
import pandas as pd

df = pd.read_csv('data/raw/Sample - Superstore.csv')
df.info()
df.head()
```

## Pasos recomendados para el EDA

1. Exploración inicial

- Cargar datos con pandas.
- Revisar valores faltantes y tipos de datos.
- Analizar la distribución de Sales, Profit y Discount.
- Identificar productos y clientes top (por ventas y por margen).

2. Limpieza y preparación

- Convertir fechas (`Order Date`, `Ship Date`) con `pd.to_datetime`.
- Crear columnas derivadas: `order_year`, `order_month`, `profit_margin` (por ejemplo, Profit / Sales), `shipping_time_days`.
- Filtrar y corregir registros inconsistentes (envíos anteriores al pedido, valores negativos no esperados).

3. Análisis exploratorio

- Ventas y ganancias por Región y Estado.
- Ventas y ganancias por Categoría y Subcategoría.
- Análisis por Segmento de cliente.
- Relación entre `Discount` y `Profit` (¿los descuentos reducen la rentabilidad?).
- Detectar productos con devoluciones o pérdidas recurrentes.

4. Visualización

- Barras y gráficos de pastel para proporciones (categorías, segmentos).
- Scatter plot `Sales` vs `Profit` para de cliente es más rentable?
