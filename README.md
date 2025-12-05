# Análisis Automatizado

Herramienta de análisis de datos que genera reportes profesionales utilizando análisis estadístico, visualizaciones y generación de insights con la API de Claude (Anthropic).

## Descripción

Este proyecto analiza automáticamente archivos CSV y genera:
- Estadísticas descriptivas completas
- Visualizaciones (histogramas, boxplots, heatmaps, gráficos de barras)
- Detección de outliers
- Análisis de correlaciones
- Reporte ejecutivo generado con IA (Claude)

## Dataset Ejemplo

- **Nombre:** Wine Quality - White Wine
- **Registros:** 4,898
- **Columnas:** 12 (todas numéricas)
- **Fuente:** UCI Machine Learning Repository

### Variables del dataset:
| Variable | Descripción | Tipo |
|----------|-------------|------|
| fixed acidity | Acidez fija (g/L) | Numérica |
| volatile acidity | Acidez volátil (g/L) | Numérica |
| citric acid | Ácido cítrico (g/L) | Numérica |
| residual sugar | Azúcar residual (g/L) | Numérica |
| chlorides | Cloruros (g/L) | Numérica |
| free sulfur dioxide | SO2 libre (mg/L) | Numérica |
| total sulfur dioxide | SO2 total (mg/L) | Numérica |
| density | Densidad (g/cm³) | Numérica |
| pH | pH | Numérica |
| sulphates | Sulfatos (g/L) | Numérica |
| alcohol | Alcohol (% vol) | Numérica |
| quality | Calidad (0-10) | Categórica |

## Requisitos Previos

1. Python 3.9 o superior
2. Cuenta en Anthropic (para API de Claude)

## Instalación

### 1. Clonar el repositorio
```bash
git clone https://github.com/YahwthaniMG/Ciencia_Datos_P3.git
cd Ciencia_Datos_P3
```

### 2. Crear entorno virtual (recomendado)
```bash
python -m venv venv
source venv/bin/activate  # Linux/Mac
# o
venv\Scripts\activate  # Windows
```

### 3. Instalar dependencias
```bash
pip install -r requirements.txt
```

### 4. Configurar API Key de Claude

#### Opción A: Usando archivo .env (recomendado)
Crea un archivo env: 
```bash
example.env
```
El archivo `.env` debe contener:
```bash
ANTHROPIC_API_KEY="tu_api_key_aqui"
```
#### Opción B: Variable de entorno del sistema
```bash
# Linux/Mac
export ANTHROPIC_API_KEY="tu_api_key_aqui"

# Windows (PowerShell)
$env:ANTHROPIC_API_KEY="tu_api_key_aqui"
```

### 5. Obtener API Key de Anthropic

1. Ir a [console.anthropic.com](https://console.anthropic.com)
2. Crear una cuenta o iniciar sesión
3. Ir a "API Keys" en el menú
4. Crear una nueva API key
5. Copiar la key (solo se muestra una vez)

## Uso

### Ejecutar el Notebook
```bash
jupyter notebook automated_analysis_v1.ipynb
jupyter notebook automated_analysis_v2.ipynb // Si deseas utilizar ML
```

### Estructura del análisis:
1. **Carga y validación de datos**
2. **Análisis estadístico descriptivo**
3. **Visualizaciones**
   - Histogramas para variables numéricas
   - Boxplots para detección de outliers
   - Gráficos de barras para variables categóricas
   - Heatmap de correlaciones
   - Heatmap de valores faltantes
4. **Análisis de correlaciones**
5. **Generación de insights con Claude**
6. **Reporte final**

## Estructura del Proyecto

```
Ciencia_Datos_P3/
├── .env          # Archivo para variables de entorno
├── .gitignore           # Archivos excluidos de Git
├── README.md            # Este archivo
├── requirements.txt     # Dependencias de Python
├── data/
│   └── winequality-white.csv
├── automated_analysis_v1.ipynb  # Notebook principal (Analisis sin ML)
├── automated_analysis_v2.ipynb  # Notebook secundario (Analisis con ML)
├── outputs/             # Gráficas generadas
└── reports/             # Reportes txt generados (Tip: Cambia la extension a md)
```

## Uso de la API de Claude

El proyecto utiliza la API de Claude para generar insights automáticos. Ejemplo de uso:

```python
from anthropic import Anthropic
from dotenv import load_dotenv
import os

# Cargar variables de entorno
load_dotenv()

# Inicializar cliente
client = Anthropic(api_key=os.getenv("ANTHROPIC_API_KEY"))

# Generar insights
response = client.messages.create(
    model="claude-sonnet-4-20250514",
    max_tokens=2000,
    messages=[
        {"role": "user", "content": "Analiza estos datos..."}
    ]
)

print(response.content[0].text)
```

## Equipo

### TEAM SOPO:
- [Yahwthani](https://github.com/YahwthaniMG)
- [Sebastian](https://github.com/0247473)
- [Gabriel Z](https://github.com/GabrielZaidUP)
- [Gabriel T](https://github.com/GTorreZac)

## Licencia

Este proyecto es para fines educativos.

## Referencias

- [Kaggle - White Wine Quality](https://www.kaggle.com/datasets/piyushagni5/white-wine-quality?select=winequality-white.csv)
- [Documentación de Anthropic](https://docs.anthropic.com)
