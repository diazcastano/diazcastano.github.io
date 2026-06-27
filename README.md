# Urban Mobility and Economic Productivity in Cities Across Latin America
# importar librerías
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt

#cargar archivos
traffic = pd.read_csv('/datasets/tomtom_traffic.csv´)
eco = pd.eco_csv('/datasets/oecd_city_economy.csv')

*EXPLORACION DE DATOS*

#mostrar las primeras 5 filas de traffic
traffic.head(5)
#mostrar las primeras 5 filas de eco
eco.head(5)

#examinar la estructura de traffic
traffic.info( ) 
display(traffic.head(3))

En la estructura del DF traffic, se observa que:
- Las columnas 'UpdateTimeUTC' y 'UpdateUTCWeekAgo' son de tipo object, se deben cambiar a datetime, las demás columnas están bien tipificadas.
- No se encuentran valores nulos en el dataframe Traffic.

# Examinar la estructura de eco
eco.info()
display(eco.head(3))

En la estructura del DF eco, se observa que: 
- Las columnas 'City GDP/capita', 'Unemployment %', 'PM2.5' y 'Population' son tipo object, cuando deberían ser float64, se deben cambiar a este formato; esto puede deberse a que no se estandariza el signo para definir decimales, además de que el signo % hace parte de los valores de unemployment, lo que puede generar confusión.
- No se encuentran valores nulos en el dataframe Eco.

# Estandarización de nombres de columnas a snake_case
traffic = traffic.rename(columns=("Country":"country","City":"city","UpdateTimeUTC":"update_time_utc","JamsDelay":"jams_delay","TrafficIndexLive":"traffic_index_live"
