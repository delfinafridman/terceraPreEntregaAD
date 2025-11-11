Proyecto: Análisis Exploratorio y Preparación de Datos de Reservas Hoteleras
Descripción
Este proyecto se centra en el Análisis Exploratorio de Datos (EDA) y la Preparación de Datos de un dataset de reservas hoteleras, con el objetivo de optimizar la calidad y consistencia del conjunto de datos previo a la modelización.
 El enfoque principal está en detectar patrones, correlaciones, valores atípicos y nulos, asegurando una base sólida para etapas analíticas posteriores, como la predicción de cancelaciones y el diseño de estrategias comerciales.
Dataset utilizado
Fuente: Hotel Booking Cancellation Prediction – Kaggle


Descripción: contiene información detallada sobre reservas hoteleras, incluyendo datos del cliente, características del hotel, tipo de habitación, fechas, duración, anticipación, precio promedio, estado de la reserva (cancelada o no), entre otros.
Contexto de negocio
El proyecto simula el caso de un servicio hotelero que busca optimizar su gestión de reservas mediante el análisis del comportamiento de sus clientes.
 Los objetivos de negocio incluyen:
Reducir el impacto económico de las cancelaciones recurrentes.


Predecir la probabilidad de cancelación para ajustar políticas y descuentos.


Identificar patrones de comportamiento en clientes y segmentos del mercado.
Se plantea, además, el diseño de estrategias basadas en perfiles de clientes con mayor o menor propensión a cancelar.
Hipótesis analizadas
H1: El segmento del mercado influye en el tipo de habitación reservada.
Se realiza un Test de independencia (Chi-cuadrado) entre market_segment y reserved_room_type. Se rechaza la hipótesis nula. El segmento del mercado influye en el tipo de habitación reservada.


H2: Un precio promedio alto tiene una relación directa con las cancelaciones. 
Test de diferencia de medias (t-test) entre adr en reservas canceladas y no canceladas. Se rechaza la hipótesis nula. Un precio promedio alto tiene una relación directa con las cancelaciones.


H3: La cantidad de noches reservadas se relaciona con el precio.
Correlación de Pearson entre adr y total nights. Se rechaza la hipótesis nula. La cantidad de noches reservadas se relaciona con el precio.


H4: La cantidad de noches reservadas se relaciona con el precio. 
Análisis de varianza (ANOVA) entre lead_time y is_canceled.Se rechaza la hipótesis nula. El tipo de 'lead' afecta la tasa de cancelación.
Exploración y limpieza
Valores nulos:
A partir del test de Little llegamos a que los datos faltantes no son completamente random por lo que optamos por imputar con KNN los datos faltantes de 'children', 'country' y 'agent'. 
Valores atípicos:
Decisión de no eliminar outliers en variables clave como adr (precio promedio), ya que reflejan picos de tarifas estacionales y reservas grupales.


Duplicados:


Eliminados registros repetidos para evitar sesgos en conteos.


Preparación de variables
Encoding:


Variables categóricas (como market_segment, meal, hotel) convertidas con one-hot encoding.


Escalamiento:


Utilizamos Standard Scaler para estandarizar las variables excluyendo las columnas 'agent' porque es un Id, 'is_canceled' porque es el target,y  'arrival_date_year' porque es una fecha.
Dashboard exploratorio en Power BI
Principales visualizaciones desarrolladas:
Distribución de reservas por segmento de mercado y tipo de habitación; vinculado al estado de cancelación. 


Comparativa de precios promedio (ADR) según estado de cancelación; las tarifas más altas tienen mayor propensión a cancelación 


Análisis de composición de grupos (adultos/niños) y estacionalidad de estadías: la mayoría de los grupos están compuestos por adultos o incluso en su totalidad. La mayor cantidad de estadías fueron en julio y agosto mientras que Enero y Noviembre la menor cantidad.

Evolución temporal de cancelaciones por mes; varía igual que la cantidad de estadías
Cancelación según si el huésped es repetido: la probabilidad de cancelación es mayor si el huésped es nuevo 
Insight principal:
La tasa de cancelación se ve relacionada a la condición del huésped, si ya se hospedó o no. Además el precio de la habitación, combinado con el tipo adhieren información a la creación de un perfil con mayor probabilidad de cancelación. La estacionalidad está vinculada a la cantidad de huéspedes y la composición del grupo (niños, adultos y bebés) ambas no se relacionan con la cancelación.
