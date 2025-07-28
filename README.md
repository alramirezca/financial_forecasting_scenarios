# Introducción al Proyecto de Pronóstico de Cuentas Financieras

## 🚀 Introducción
El presente proyecto tiene como objetivo principal desarrollar y aplicar **modelos de pronóstico trimestral** para las cuentas de **Facturación** y **Saldo** de Tuya, abarcando los años **2025, 2026 y 2027**. 

Esto se realiza en el marco de las pruebas de resistencia que la compañía presenta anualmente ante la **Superintendencia Financiera de Colombia**, buscando evaluar la resiliencia de la entidad ante escenarios económicos adversos y asegurar su estabilidad, solvencia y liquidez. 

Adicionalmente, se explorarán **metodologías de estimación avanzadas** con el fin de mejorar la precisión de los pronósticos, superando las métricas exigidas por la Superintendencia y reduciendo el error por debajo del 10%.

---

## 🏛️ Alcance del Proyecto
El alcance de este proyecto se centra en la generación de pronósticos para las cuentas de **Facturación** y **Saldo** bajo tres escenarios distintos: 

- **Base**  
- **Adverso**  
- **Alterno**

Estos escenarios incorporarán impactos macroeconómicos relevantes, con especial énfasis en el cumplimiento de las normativas de la Superintendencia Financiera. 

Se analizará la relación entre los diferentes escenarios (**Escenario Base > Escenario Adverso > Escenario Alterno**) y se presentarán los resultados de manera que se visualicen claramente estas trayectorias futuras.

### Expectativas del Comité
- **+25%** en la facturación de diciembre de 2027 respecto a diciembre de 2024.
- **−3%** en la facturación de junio de 2026 respecto a diciembre de 2025.
- **−3%** en la facturación de junio de 2027 respecto a diciembre de 2026.
- **+15%** en el saldo de diciembre de 2027 respecto a diciembre de 2024.

---

## 🧠 Metodología General
La metodología a seguir en este proyecto se estructurará en las siguientes fases generales las cuales se encuentran detalladas y estructuradas en los notebooks denominados con incisos similares:

1. **Análisis Exploratorio de Datos (EDA)**  
   Se realizará una exploración de las hojas **"BASE"** y **"MACROS"** del archivo Excel proporcionado para comprender la estructura de los datos, identificar la estadistica descriptiva basica, patrones, tendencias, anomalías y la relación entre las variables de Facturación y Saldo con las variables macroeconómicos.

2. **Selección de Características**  
   Se identificarán y seleccionarán las variables más relevantes para la construcción de los modelos de pronóstico, incluyendo la incorporación de variables macroeconómicas que ofrezcan una explicabilidad y sentido lógico con las cuentas a modelar, acorde con la realidad del negocio y a la disponibilidad de las mismas.

3. **Entrenamiento de Modelos**  
   Se procederá al entrenamiento de diferentes modelos de pronóstico como Prophet, Sarimax y regresión lineal ridge. El objetivo final es construir dos nuevos modelos que busquen mejorar la precisión y reducir el error por debajo del 10%.

4. **Evaluación de Escenarios**  
   Finalmente, se realizará la evaluación de los modelos bajo los escenarios **Base**, **Adverso** y **Alterno**.  
   Se generarán los pronósticos trimestrales para los años 2025, 2026 y 2027, y se presentarán los resultados de manera clara y comprensible, destacando las trayectorias futuras de las cuentas de Facturación y Saldo en cada escenario.


## 📝 Conclusiones descritas en los notebooks

A partir del **Análisis Exploratorio de Datos (EDA)** realizado sobre las bases de información disponibles, se destacan los siguientes hallazgos y consideraciones relevantes para la construcción de los modelos de pronóstico:

---

### Alertas Principales – Base de Datos

1. **Correlaciones Altas Entre Variables**
   - `aumento_recaudo` presenta una correlación muy alta con `dummy_colocaciones`.
   - `desembolsos` está fuertemente correlacionado con `estrategia_credicompras` y otras dos variables.
   - `dummy_colocaciones` muestra alta correlación con `aumento_recaudo`.
   - `estrategia_credicompras` se encuentra altamente correlacionada con `desembolsos`.
   - `facturacion` presenta alta correlación con `desembolsos` y otra variable adicional.
   - `saldo` presenta alta correlación con `desembolsos` y otra variable adicional.

2. **Calidad y Cantidad de Datos**
   - `facturacion` tiene 12 valores faltantes (25% del total).
   - `saldo` tiene 12 valores faltantes (25% del total).
   - `desembolsos` contiene 10 valores iguales a cero (20,8% del total).
   - Solo se dispone de **36 registros** para las variables `facturacion` y `saldo`.

---

### Alertas Principales – Variables Macroeconómicas
- Se identifican **altas correlaciones entre las variables macroeconómicas**.
- El número de observaciones disponibles para estas variables también es **36 registros**, lo cual limita el tamaño de la muestra para los análisis y los modelos.

---

### Tendencias de Facturación y Saldos
- La **volatilidad trimestral (QoQ)** de la facturación es elevada, con caídas pronunciadas en 2020, probablemente asociadas a factores macroeconómicos externos.
- Desde 2021, la facturación muestra un **repunte importante**, con una tendencia a estabilizarse hacia 2023, evidenciando una fase de maduración posterior a la recuperación.
- El **crecimiento anual (YoY)** resulta más estable y menos volátil que el QoQ, reforzando la importancia de evaluar ambas perspectivas.
- La variable **Saldo** muestra **mayor estabilidad y menor variabilidad** frente a Facturación, lo que sugiere una mayor resiliencia a cambios abruptos en el entorno.

---

### Análisis de Escenarios
La definición de escenarios permite evaluar la resiliencia financiera de Tuya ante distintas condiciones económicas:

- **Escenario Pesimista:** Refleja las condiciones más desfavorables y riesgosas.
- **Escenario Base:** Representa la trayectoria central esperada bajo supuestos actuales.
- **Escenario Optimista:** Considera una evolución más positiva que el escenario base, con mejoras graduales en las condiciones económicas.
- **Escenario Alterno:** Proyecta el mejor comportamiento posible, donde los resultados superan las expectativas iniciales.

---

### Correlación con Variables Macroeconómicas
El análisis confirma una **alta dependencia de las cuentas de Facturación y Saldo respecto a las condiciones macroeconómicas**:

#### Facturación
- Fuerte correlación positiva con el **crecimiento del PIB** en todos los escenarios.
- Correlación moderada con **inflación** y, en menor medida, con la **tasa de cambio**.
- Correlación negativa moderada con la **tasa de desempleo**, coherente con la expectativa de que mayores niveles de desempleo reducen el consumo y afectan la facturación.

#### Saldo
- La **tasa de cambio** (en todas sus variantes) muestra la correlación más fuerte con esta variable, evidenciando la importancia de la exposición cambiaria.
- Relación positiva significativa con **inflación** y **PIB**, aunque menos intensa que en el caso de la facturación.
- Correlación más baja con tasas de interés (DTF, IBR, REPO), lo cual indica que estas variables tienen un impacto secundario en comparación con la tasa de cambio y el PIB.


### Conclusiones Finales del EDA

- **Modelado con enfoques simples:**  
  Se optará por el uso de modelos relativamente simples como **SARIMAX**, **Prophet** y **Regresión Lineal Ridge**, dado que el número de observaciones disponibles es reducido y no permite el uso efectivo de modelos más complejos o de machine learning clásico.

- **Exclusión de variables dummies y desembolsos:**  
  Las variables **dummies** y **desembolsos** serán descartadas debido a la ausencia de información histórica suficiente y a la necesidad de aplicar métodos de imputación complejos para escenarios y años en los que no existen datos.  
  Por tanto, para la base interna solo se utilizarán **facturación** y **saldo**, las cuales constituyen las variables objetivo (target).

- **Selección robusta de variables macroeconómicas:**  
  En cuanto a las variables macroeconómicas, se emplearán técnicas más avanzadas de **selección de características** que permitan identificar los factores más relevantes y guiar la toma de decisiones en el modelado.

- **Entrenamiento mediante validación cruzada temporal:**  
  Debido a la **escasez de datos disponibles**, el uso de un esquema tradicional de *train-test split* no resulta adecuado, ya que reduce de forma considerable la cantidad de información disponible para el entrenamiento.  
  Para optimizar el aprovechamiento del histórico, se utilizará **TimeSeriesSplit** como técnica de validación cruzada.  
  Este método permite evaluar los modelos respetando la secuencia temporal de los datos y asegurando que el entrenamiento siempre se realice con información del pasado y las pruebas con datos futuros.

## 🔍 Selección de Características

### Enfoque aplicado
En la construcción de modelos predictivos, la **selección de características** es una etapa clave para garantizar que los modelos sean robustos, eficientes y eviten el sobreajuste.  
Dado que las bases de datos suelen incluir múltiples variables que pueden describir el mismo fenómeno, este proceso busca **identificar las variables más relevantes y eliminar aquellas redundantes o poco informativas**.

---

### Estrategia utilizada
El procedimiento seguido se centró en:

1. **Evaluación de la multicolinealidad:**  
   Se analizaron las correlaciones entre variables para detectar redundancias.  
   Cuando dos o más variables mostraron una correlación muy alta, se consideró que aportaban información similar.

2. **Selección basada en información mutua:**  
   Para cada grupo de variables altamente correlacionadas, se utilizó la **información mutua** con la variable objetivo como criterio de selección.  
   La información mutua mide la dependencia entre dos variables y nos indica cuánto conocimiento adicional sobre la variable objetivo aporta una variable específica.  
   De este modo, se conservó la variable que maximiza la información mutua con el target, garantizando mayor relevancia predictiva.

---

### Resultados del proceso
Tras aplicar este método, se definieron los conjuntos óptimos de variables para cada cuenta a pronosticar:

- **Para Facturación:**  
  - `Desempleo`  
  - `Tasa_Cambio`  
  - `TASA REPO`  
  - `PIB (var. % anual, nominal)`

- **Para Saldo:**  
  - `Desempleo`  
  - `Tasa_Cambio`  
  - `TASA REPO`  
  - `CH2`

---

### Beneficios obtenidos
Este proceso permitió:
- Reducir la **complejidad del modelo** al trabajar solo con las variables más relevantes.
- Disminuir el riesgo de **sobreajuste** (overfitting).
- Mejorar la **capacidad de generalización** de los modelos y aumentar la precisión de los pronósticos.


## ⚙️ Entrenamiento de Modelos

El proceso de entrenamiento de los modelos se desarrolló siguiendo una serie de pasos ordenados y metodológicos, desde la preparación de los datos hasta la generación de pronósticos finales. A continuación, se describe cada etapa:

---

## ⚙️ Entrenamiento de Modelos

El proceso de entrenamiento de los modelos se desarrolló siguiendo una serie de pasos ordenados y metodológicos, desde la preparación de los datos hasta la generación de pronósticos finales. A continuación, se describe cada etapa:

---

### 1. Carga y preparación de los datos
- Se consolidaron las diferentes fuentes de información (macroeconómicas y base interna) en un único conjunto de datos, utilizando **Fecha** como llave de integración.
- La columna de fecha se estableció como índice principal y se ordenaron los registros cronológicamente.
- Se calcularon las variables objetivo como los **cambios porcentuales (pct_change)** de las columnas `facturacion` y `saldo`, permitiendo modelar las variaciones relativas en lugar de los valores absolutos.

---

### 2. Definición de features y targets
- **Features (variables predictoras):**
  - Para **Facturación**: `Desempleo`, `Tasa_Cambio`, `TASA REPO`, `PIB (var. % anual, nominal)`
  - Para **Saldo**: `Desempleo`, `Tasa_Cambio`, `TASA REPO`, `CH2`
- **Targets (variables objetivo):**
  - `facturacion_change`
  - `saldo_change`
- Se eliminaron las filas con valores nulos en cualquiera de estas variables críticas, garantizando consistencia e integridad en los datos.

---

### 3. Escalado de los datos
- **Variables predictoras:** escaladas mediante `StandardScaler` para normalizar las magnitudes (media = 0, desviación estándar = 1).
- **Variables objetivo:** escaladas con `MinMaxScaler` a un rango [0, 1] para favorecer la estabilidad y mejorar la interpretación de algunos algoritmos.

---

### 4. Validación cruzada temporal
- Se implementó **TimeSeriesSplit (3 divisiones)** para evaluar el desempeño de los modelos sin romper la secuencia temporal.
- Este método garantiza que los datos futuros nunca se utilicen en el entrenamiento, evitando fuga de información y asegurando evaluaciones realistas.

---

### 5. Métrica de evaluación
- En cada división se calcula el **RMSE (Root Mean Squared Error)**.
- Como métrica final se utiliza la **mediana de los RMSE** obtenidos, ya que es robusta frente a valores atípicos.

---

### 6. Modelos evaluados
Se probaron tres familias de modelos:

1. **Ridge Regression**  
   Modelo lineal regularizado (L2) para capturar relaciones lineales y controlar el sobreajuste.
2. **SARIMAX**  
   Modelo autorregresivo integrado con medias móviles y regresores exógenos, adecuado para series temporales con estacionalidad y tendencias.
3. **Prophet**  
   Modelo aditivo diseñado para series con tendencias no lineales y múltiples estacionalidades, que permite incluir regresores externos.

---

### 7. Optimización de hiperparámetros con Optuna
- Se utilizó **Optuna** para la búsqueda bayesiana de los hiperparámetros más adecuados para cada modelo:
  - **Ridge Regression:**  
    - `alpha` (grado de regularización L2)
  - **SARIMAX:**  
    - `p`, `d`, `q` (parámetros autorregresivos, diferenciales y de medias móviles)
    - `seasonal_order` (componentes estacionales si aplica)
  - **Prophet:**  
    - `changepoint_prior_scale` (sensibilidad a cambios en la tendencia)
    - `seasonality_prior_scale` (peso de la estacionalidad)

---

### 8. Comparación de modelos
- Se compararon los **RMSE** obtenidos por cada modelo para `facturacion_change` y `saldo_change`.
- Se seleccionó el modelo con menor RMSE como el de mejor desempeño para cada target.
- Los resultados se presentaron mediante tablas y gráficos para facilitar la interpretación.

---

### 9. Resultados por fold
- Además de la métrica global, se documentaron los RMSE individuales de cada fold.
- Este análisis permite evaluar la **estabilidad y consistencia** del modelo a lo largo del tiempo.

---

### 10. Entrenamiento final
- El modelo seleccionado como mejor para cada target se reentrenó con **todo el histórico disponible**.
- Con estos modelos definitivos se generaron **predicciones históricas (backtesting)** para evaluar su ajuste sobre los datos conocidos.

---

### 11. Predicciones históricas de todos los modelos
- También se generaron predicciones con los tres modelos (Ridge, SARIMAX y Prophet) sobre todo el conjunto de datos.
- Se graficaron junto a los valores reales para comparar su comportamiento y ajuste visualmente.

---

### 12. Ensemble de modelos
- Se implementó un **ensemble simple (promedio)** combinando las predicciones de los tres modelos.
- Este enfoque aprovecha las fortalezas de cada modelo individual, buscando reducir el error general y lograr un pronóstico más robusto.

---

### 13. Evaluación con MAPE (Mean Absolute Percentage Error)
Se calculó el **MAPE** para los cuatro modelos (incluyendo el ensemble) y para las dos variables objetivo. Los resultados fueron:

| Target       | Ridge  | SARIMAX | Prophet | Ensemble |
|--------------|--------|---------|---------|----------|
| **Facturación** | 138.12 | 178.08  | 139.33  | 124.56   |
| **Saldo**       | 126.88 | 115.04  | 135.32  | 85.29    |

Ninguno de los modelos logró alcanzar el objetivo de un error inferior al 10%. Esto se debe principalmente a la **limitada cantidad de datos históricos disponibles**.  
Los errores podrían reducirse si se implementan:
1. Más variables exógenas (features internas y externas adicionales).
2. Un mayor historial de datos trimestrales.
3. Estrategias avanzadas de **ingeniería de características** (transformaciones logarítmicas, interacciones, medias móviles, entre otras).

Estas estrategias no se aplicaron en esta fase debido al tiempo limitado y al carácter exploratorio de este ejercicio.

---

### 14. Almacenamiento del pipeline
Todo el pipeline resultante para los cuatro modelos optimizados se almacenó en formato **.pkl**, permitiendo su reutilización en futuras etapas del proyecto.


## Evaluación de Escenarios

Tras la generación de los pronósticos se procede a evaluar el cumplimiento de los hitos definidos para el negocio en el escenario Base, así como analizar la evolución de los escenarios Pesimista y Alterno. La comparación se realiza para las dos variables objetivo: **Facturación** y **Saldo**.

### Resultados de Validación para Saldo

| Modelo                 | Hito              | Pred (%)   | Hito a cumplir (%) | Error (%)     | Cumple     |
|------------------------|-------------------|------------|--------------------|---------------|------------|
| saldo_ridge_abs       | 27_vs_24          | -13.38     | 15.0              | -28.38        | No cumple  |
| saldo_ridge_abs       | jun26_vs_dic25    | -2.07      | NaN               | NaN           | None       |
| saldo_ridge_abs       | jun27_vs_dic26    | -2.34      | NaN               | NaN           | None       |
| saldo_sarimax_abs     | 27_vs_24          | -74.99     | 15.0              | -89.99        | No cumple  |
| saldo_sarimax_abs     | jun26_vs_dic25    | -22.16     | NaN               | NaN           | None       |
| saldo_sarimax_abs     | jun27_vs_dic26    | -24.27     | NaN               | NaN           | None       |
| saldo_prophet_abs     | 27_vs_24          | -51.52     | 15.0              | -66.52        | No cumple  |
| saldo_prophet_abs     | jun26_vs_dic25    | -12.01     | NaN               | NaN           | None       |
| saldo_prophet_abs     | jun27_vs_dic26    | -13.07     | NaN               | NaN           | None       |
| saldo_ensemble_abs    | 27_vs_24          | -52.26     | 15.0              | -67.26        | No cumple  |
| saldo_ensemble_abs    | jun26_vs_dic25    | -12.27     | NaN               | NaN           | None       |
| saldo_ensemble_abs    | jun27_vs_dic26    | -13.46     | NaN               | NaN           | None       |

**Análisis:**  
Para la variable **Saldo**, ninguno de los modelos ni el ensemble lograron cumplir el hito de crecimiento del 15 % para el periodo 2027 vs. 2024. Todos los modelos proyectan una disminución significativa, con el modelo Ridge siendo el que predice una caída menos pronunciada (-13.38 %). Los hitos intermedios (junio 2026 vs. diciembre 2025 y junio 2027 vs. diciembre 2026) no contaban con un valor de referencia establecido (NaN).

---

### Resultados de Validación para Facturación

| Modelo                       | Hito              | Pred (%)   | Hito a cumplir (%) | Error (%)     | Cumple     |
|------------------------------|-------------------|------------|--------------------|---------------|------------|
| facturacion_ridge_abs       | 27_vs_24          | 436.11     | 25.0              | 411.11        | No cumple  |
| facturacion_ridge_abs       | jun26_vs_dic25    | 29.24      | -3.0              | 32.24         | No cumple  |
| facturacion_ridge_abs       | jun27_vs_dic26    | 38.04      | -3.0              | 41.04         | No cumple  |
| facturacion_sarimax_abs     | 27_vs_24          | 713.39     | 25.0              | 688.39        | No cumple  |
| facturacion_sarimax_abs     | jun26_vs_dic25    | 38.58      | -3.0              | 41.58         | No cumple  |
| facturacion_sarimax_abs     | jun27_vs_dic26    | 50.50      | -3.0              | 53.50         | No cumple  |
| facturacion_prophet_abs     | 27_vs_24          | 103.65     | 25.0              | 78.65         | No cumple  |
| facturacion_prophet_abs     | jun26_vs_dic25    | -4.13      | -3.0              | -1.13         | Cumple     |
| facturacion_prophet_abs     | jun27_vs_dic26    | -1.26      | -3.0              | 1.74          | Cumple     |
| facturacion_ensemble_abs    | 27_vs_24          | 355.16     | 25.0              | 330.16        | No cumple  |
| facturacion_ensemble_abs    | jun26_vs_dic25    | 20.50      | -3.0              | 23.50         | No cumple  |
| facturacion_ensemble_abs    | jun27_vs_dic26    | 28.10      | -3.0              | 31.10         | No cumple  |

**Análisis:**  
Para la variable **Facturación**, el modelo Prophet es el único que logra cumplir con los hitos de decrecimiento del -3 % para los periodos intermedios (junio 2026 vs. diciembre 2025 y junio 2027 vs. diciembre 2026). Sin embargo, para el hito general 2027 vs. 2024 (25 %), todos los modelos, incluido Prophet, predicen un crecimiento muy superior, resultando en un "No cumple". Esto indica que Prophet captura mejor los cambios a corto plazo, pero su proyección a largo plazo difiere significativamente de las expectativas.

---

### Conclusiones finales de los escenarios (Modelo Ensemble)

El análisis detallado de los escenarios se realiza a partir del **modelo Ensemble**, seleccionado por presentar el **menor error MAPE** durante el entrenamiento y validación cruzada. Las principales conclusiones son:

#### Facturación
- Los tres escenarios muestran **tendencias crecientes** durante el horizonte 2025–2027.
- **Pesimista:** Crecimiento continuo, alcanzando valores cercanos al 28 % en 2027, con picos en 2026 (≈26 %).
- **Alterno:** Presenta una **contracción fuerte en 2026** (caída de -21 %), seguida de una recuperación hasta 21 % al cierre de 2027.
- **Base:** Evolución intermedia, con un crecimiento estable y sostenido, llegando a 21 % en 2027.

#### Saldo
- A diferencia de la facturación, los escenarios de saldo mantienen valores **negativos durante todo el periodo**.
- **Pesimista:** Caídas moderadas entre -6 % y -5 %, con ligera mejora en 2026, pero sin alcanzar valores positivos.
- **Alterno:** La mayor contracción, hasta -14.5 % en marzo de 2026, con recuperación posterior, cerrando 2027 en -7 %.
- **Base:** Evolución similar al pesimista, con caídas suaves pero persistentes (entre -7 % y -5.6 %), cerrando 2027 en -7 %.

#### Interpretación general
- **Comportamiento divergente:** La **Facturación crece en todos los escenarios**, mientras que el **Saldo permanece en terreno negativo**.
- **Alta incertidumbre:** Los escenarios evidencian vulnerabilidad en la evolución del saldo y la dependencia de la facturación frente a las condiciones macroeconómicas (especialmente en 2026).
- Es fundamental incorporar más información y variables exógenas en futuras iteraciones para reducir la incertidumbre y mejorar la capacidad predictiva.

---




 






