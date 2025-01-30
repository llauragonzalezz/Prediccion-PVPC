# Predicción del PVPC en España por Periodo (Punta, Llano, Valle) con Aprendizaje Automático

**Asignatura**: Aprendizaje Automático en Series Temporales y Flujos de Datos 
**Fecha**: Octubre 2024  

## Descripción del Proyecto

Este proyecto tiene como objetivo predecir el Precio Voluntario para el Pequeño Consumidor (PVPC) en España utilizando técnicas de aprendizaje automático aplicadas a series temporales. La predicción se realiza por periodos horarios (punta, llano y valle), utilizando datos históricos de precios de la electricidad junto con variables exógenas como demanda eléctrica y precios de carburantes.


## Contenidos del Repositorio
- `data/`: Contiene los datos históricos de PVPC y los lags utilizados en la modelización. Los lags representan valores pasados del PVPC que se emplean como predictores en los modelos de forecasting.
- `data_preparation/`: Contiene los datos de las variables exógenas utilizadas para el análisis y un Notebook para unificar todos los datos.
- `autocorrelation.ipynb`: Realiza un análisis de autocorrelación en los datos de precios de la electricidad. Se examina la relación de los valores actuales con los pasados para determinar patrones temporales en los tramos horarios de PVPC.
- `correlations.ipynb`: Contiene la preparación de datos y un análisis de correlación entre distintas variables exógenas y el precio de la electricidad. 
- `PVPC_SKForecast.ipynb`: Implementa modelos de predicción para el PVPC. Se entrenan y evalúan modelos basados en regresión, incorporando técnicas de backtesting y optimización de hiperparámetros.


## Tecnologías y Librerías Utilizadas
- **Python 3.9+**
- **Pandas** (para la manipulación de datos)
- **Scikit-learn** (para modelos de regresión y evaluación)
- **Skforecast** (para adaptación de modelos de regresión a forecasting)
- **XGBoost** y **Random Forest** (para modelos avanzados de predicción)
- **Matplotlib y Seaborn** (para visualización de datos)

## Datos Utilizados
Los datos incluyen:
- PVPC diario por periodo horario (fuente: Red Eléctrica Española).
- Demanda eléctrica en los tramos punta, llano y valle.
- Precios diarios de carburantes (fuente: CNMC).
- Datos climáticos (temperatura, humedad, radiación, precipitaciones, entre otros).

## Metodología
1. **Exploración de datos:** Análisis de series temporales y selección de variables exógenas.
2. **Modelado:**
   - Modelos autorregresivos recursivos con distintas técnicas (DecisionTreeRegressor, RandomForestRegressor, XGBRegressor, ARIMA, etc.).
   - Evaluación mediante **backtesting** con 7 steps y 20 folds.
   - **Optimización de hiperparámetros** con Grid Search.
   - Incorporación de **variables exógenas** para mejorar la predicción.
3. **Evaluación:**
   - Comparación de modelos según el Error Cuadrático Medio (MSE).
   - Validación de predicciones en conjunto de test.

## Resultados
- **Los datos climaticos** no mostraron una relación significativa con el PVPC, por lo que fueron descartados como variables exógenas
- **El mejor modelo identificado** fue una combinación de RandomForestRegressor y XGBRegressor optimizados con hiperparámetros y utilizando variables exógenas.
- **La inclusión de variables exógenas**  como la demanda eléctrica y el precio de la gasolina mejoró significativamente la precisión de las predicciones.
- **La metodología de backtesting** permitió evaluar la capacidad de generalización de los modelos.

