# Proyecto_2: Éxito musical :notes:
En este proyecto, se llevará a cabo un análisis de validación de hipótesis utilizando una base de datos de Spotify. Para ello, emplearemos dos herramientas destacadas en el ámbito del análisis de datos: BigQuery y Power BI.

![caratula](https://github.com/user-attachments/assets/88f82157-1729-4d9e-884a-4b309e19e47d)

# Índice 
- [Introducción](#introducción)
- [Equipo 🤝](#equipo)
- [Herramientas :hammer_and_pick:](#herramientas)
- [Lenguajes](#lenguajes)
- [Procesamiento y análisis](#procesamiento-y-análisis)
  - [Procesamiento de los datos](#procesamiento-de-los-datos)
  - [Análisis exploratorio](#análisis-exploratorio)
  - [Validación de hipótesis](#validación-de-hipótesis)
- [Resultados](#resultados)
- [Conclusiones](#conclusiones)
- [Recomendaciones](#recomendaciones)
- [Enlaces](#enlaces)
  
## Introducción
En la industria musical, tomar decisiones informadas por datos se ha vuelto un recurso crucial. En este escenario, una discográfica se prepara para lanzar a un nuevo artista en el mercado musical internacional y dispone de una herramienta valiosa: un amplio conjunto de datos de Spotify con información sobre las canciones más populares de 2023.

La discográfica ha desarrollado varias hipótesis para descubrir qué factores contribuyen al éxito de una canción:
+ :one: Las canciones con un mayor BPM (Beats Por Minuto) tienen más éxito en términos de cantidad de streams en Spotify.
+ 2️⃣ Las canciones más populares en el ranking de Spotify también tienen un comportamiento similar en otras plataformas como Deezer.
+ 3️⃣ La presencia de una canción en un mayor número de playlists se relaciona con un mayor número de streams.
+ 4️⃣ Los artistas con un mayor número de canciones en Spotify tienen más streams.
+ 5️⃣ Las características de la canción influyen en el éxito en términos de streams en Spotify.

El propósito de este proyecto es verificar estas hipótesis a través del análisis de datos y ofrecer recomendaciones estratégicas fundamentadas en los resultados obtenidos, con la meta de mejorar las probabilidades de éxito del nuevo artista.

## Equipo 
- [María José L](https://github.com/mariwolves)
- [Sixnalie V](https://github.com/Naliesav)

## Herramientas
+ BigQuery  
+ Power BI
  
## Lenguajes
+ SQL
## Procesamiento y análisis
Este proceso se dividió en tres etapas, en cada una de las cuales se aplicaron técnicas y programas específicos de acuerdo con los objetivos planteados.
##  Procesamiento de los datos 
El tratamiento de los datos se realizó en BigQuery utilizando comandos SQL. Los pasos seguidos fueron los siguientes:
+ Identificar valores nulos a través COUNTIF e IS NULL.
+ Manejar datos nulos con COALESCE
+ Identificar duplicados a través de COUNT, GROUP BY, HAVING.
+ Manejar variables que no son útiles en el análisis a través de EXCEPT.
+ Identificar datos discrepantes en variables categóricas con REGEXP_REPLACE.
+ Identificar datos discrepantes con datos que superan el rango de los enteros de 32 bits con INT64.
+ Identificar datos discrepantes en variables numéricas con MAX, MIN y AVG.
+ Comprobar y modificar tipos de datos con SAFE_CAST y CAST.
+ Crear nuevas variables utilizando CONCAT, SUM y DATE.
+ Descartar filas con NOT IN
+ Construir tablas auxiliares utilizando WITH.
+ Unir las tablas utilizando LEFT JOIN.

## Análisis exploratorio
+ Agrupar datos según variables categóricas a través de tablas
+ Visualizar las variables categóricas a través de gráficos de barras y líneas 
+ Aplicar medidas de tendencia central y dispersión (avg, median, max, min, standard deviation) en BPM, Playlists en spotify, Charts en spotify, Charts en Apple/Deezer/Shazam Playliststotal y Streams
+ Visualizar distribución a través de Hitogramas BPM, Playlist en spotify, Playliststotal y Streams

## Validación de hipótesis
La validación de hipótesis se realizó en BigQuery, y los resultados se visualizaron en gráficos mediante Power BI
+ Análisis de correlación entre métricas (Coeficiente de Pearson)

## Resultados
### Validación de hipótesis
  + **Hipótesis 1**: Las canciones con un mayor BPM (Beats Por Minuto) tienen más éxito en términos de cantidad de streams en Spotify.
    + **Conclusión**: :x: No existe relación entre ambas variables, prácticamente no hay relación entre las pulsaciones por minuto de una canción y su cantidad de reproducciones.
      + *Coeficiente de Pearson* (-0.002336...) Correlación negativa extremadamente débil. 
![image](https://github.com/user-attachments/assets/98e52261-f38e-4670-90f2-5cf6d04ecb93)

  + **Hipótesis 2**: Las canciones más populares en el ranking de Spotify también tienen un comportamiento similar en otras plataformas como Deezer.
    + **Conclusión**: :heavy_check_mark: Indica una relación lineal positiva moderada entre estas dos variables, lo que sugiere una considerable similitud en las preferencias de los usuarios de ambas plataformas.
      + *Coeficiente de Pearson* (0.59998...) 
![image](https://github.com/user-attachments/assets/96494bc8-a274-49f0-8ecc-5fb217911b49)

  + **Hipótesis 3**: La presencia de una canción en un mayor número de playlists se relaciona con un mayor número de streams.
    + **Conclusión**: :heavy_check_mark: Indica una relación lineal positiva fuerte entre estas dos variables, lo que sugiere que las canciones que están en más playlists tienden a recibir más streams.
      + *Coeficiente de Pearson* (0.78356...)
![image](https://github.com/user-attachments/assets/f768b9fc-0acd-42a5-91a2-3747e392818f)

  + **Hipótesis 4**: Los artistas con un mayor número de canciones en Spotify tienen más streams.
    + **Conclusión**: :heavy_check_mark: Existe una relación directa entre la cantidad de canciones que un artista tiene en Spotify y la cantidad de streams que recibe. Cuanto mayor sea el catálogo de un artista en la plataforma, mayor será la probabilidad de que acumule un mayor número de streams.
      + *Coeficiente de Pearson* (0.8907...)
![image](https://github.com/user-attachments/assets/e527ceb0-eee6-4144-a38a-3d85ce4370aa)

  + **Hipótesis 5**: Las características de la canción influyen en el éxito en términos de streams en Spotify
    + **Conclusión**: :x: Las características no influyen en el número de streams que obtiene una canción, según los resultados obtenidos (-0,...). Esto sugiere una falta de correlación lineal entre estas características y el número de streams.
      + *Coeficiente de Pearson*
      +  danceability -0.105
      +  valence -0.041
      +  energy -0.025
      +  acousticness -0.005
      +  instrumentalness -0.044
      +  liveness -0.049
      +  speechiness -0.112
![image](https://github.com/user-attachments/assets/36a69253-0969-43ca-bff1-965afdd296f0)

## Conclusiones
"El éxito de una canción o artista se basa en los siguientes aspectos:
+ **Estrategias de Distribución y Marketing:** La popularidad de una canción, medida en términos de streams, está influenciada por estrategias de distribución y marketing, tales como su inclusión en listas de reproducción destacadas, su posición en rankings y su presencia en diversas plataformas.
  ![image](https://github.com/user-attachments/assets/70cc8664-a23f-471a-a4f1-b5ebfe465d02)

+ **Volumen de Contenido:** La cantidad total de canciones de un artista está estrechamente vinculada a su éxito en términos de streams, indicando que una mayor producción de contenido puede atraer una mayor cantidad de reproducciones."
  ![image](https://github.com/user-attachments/assets/e7204507-1204-46c3-b950-0d2ce85ab253)

## Recomendaciones
Con base en las conclusiones, se recomienda:
+ **Presencia en Plataformas:** Asegúrate de estar disponible en diversas plataformas de streaming, tales como Spotify, Tidal, Apple Music, Amazon Music, Qobuz, Deezer y YouTube Music.
+ **Diversidad de Contenido:** Considera ofrecer una variedad de canciones para atraer a diferentes tipos de oyentes.



## Enlaces
### [Presentación] https://docs.google.com/presentation/d/1gDDdazi5lLMqglg3ENVL9Rzq2tfu_tS03o905YV2PRo/edit?usp=sharing
### [Dashboard] https://drive.google.com/file/d/17tVrWlrLpj_ARyI35HPiKH7dYu15fWNp/view?usp=drive_link
### [Video Loom] https://www.loom.com/share/7b38f0f5cf584448858d94e821e084b1?sid=0df93413-6658-4fed-8731-69aa239437b4





