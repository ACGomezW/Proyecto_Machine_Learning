# Proyecto Machine Learning 
***Proyecto Individual N°1_Data Science_Henry***

Este proyecto abarca una serie de pasos para desarrollar un proceso de Data Engineering sobre un dataset de videojuegos, para posteriormente disponibilizar una serie de endpoints y un modelo de recomendación de juegos utilizando Machine Learning, a través de una API.

![logo](https://www.datascience-pm.com/wp-content/uploads/2021/06/ml-ops-venn-diagram-600.png)

### Contexto
Se plantea desde los propietarios de la plataforma 'Steam Games' la necesidad de contar con los datos en una API para poder ser consumidos. Por otro lado existe la necesidad de poder realizar las consultas al modelo de recomendación para lo cual resulta necesario hacer un deploy de la API.

### Dataset
Son tres (3) dataset que poseen información acerca de juegos, reseñas y distintos atributos de los mismas, en formato JSON.Los mismos se adjuntan el el [siguiente enlace](https://drive.google.com/drive/folders/1r0yc_x2rVsMoTVIUFw3W3Zh0UaXi7wvF?usp=drive_link), ya que por su tamaño no pudieron ser agregados al presente repositorio. 


### Data Engineering
Para el trabajo de Data Engineering se procedió a efectuar una serie de transformaciones solicitadas sobre los datos. Se trabajó en primera instancia los dataset por separados, por su tamaño, en archivos de tipo Jupiter Notebook, dentro de la plataforma Collab de Google. Para su tratamiento, se siguieron los siguientes pasos:
* Se abrieron y leyeron los archivos de formato JSON en líneas separadas.
* Se analizaron y almacenaron en una lista.
* Se tomó la lista de objetos JSON, se concatenaron en un único DataFrame.
* Se desanidaron columnas anidadas.
* Se eliminaron nulos y columnas innecesarias para el análisis.
* Se corrigió formato de fechas.
* Se corrigió formato Mayúsculas y Minúsculas
* En el archivo Reviews.json, se utilizó la biblioteca NLTK (***Natural Language Toolkit***) y la función **SentimentIntensityAnalyzer** para aplicar análisis de sentimiento y clasificar la columna 'Reviews', que contiene reseñas realizadas por los usuarios de los juegos, en positivas, neutrales y negativas. 
* Se guardaron esos dataset en [tres diferentes archivos formato CSV](https://drive.google.com/drive/folders/1aivJ9Njk-SeYhs0377LfuY_aA3m83q3M?usp=drive_link).
* Posteriormente se unieron los tres dataset en uno solo, eliminando nuevamente datos duplicados, o innecesarios para el análisis.
* Se guardó la información obtenida en el archivo [Total.csv](https://drive.google.com/file/d/18QNPhP2TWKsvAgkMtoyKS85_Cd14dWgP/view?usp=drive_link)
  

### API
Se solicitó efectuar la disponibilización de los siguientes endpoints a través del Framework ***FastAPI***:

def peliculas_mes(mes): '''Se ingresa el mes y la funcion retorna la cantidad de peliculas que se estrenaron ese mes (nombre del mes, en str, ejemplo 'enero') historicamente''' return {'mes':mes, 'cantidad':respuesta}

def peliculas_dia(dia): '''Se ingresa el dia y la funcion retorna la cantidad de peliculas que se estrenaron ese dia (de la semana, en str, ejemplo 'lunes') historicamente''' return {'dia':dia, 'cantidad':respuesta}

def franquicia(franquicia): '''Se ingresa la franquicia, retornando la cantidad de peliculas, ganancia total y promedio''' return {'franquicia':franquicia, 'cantidad':respuesta, 'ganancia_total':respuesta, 'ganancia_promedio':respuesta}

def peliculas_pais(pais): '''Ingresas el pais, retornando la cantidad de peliculas producidas en el mismo''' return {'pais':pais, 'cantidad':respuesta}

def productoras(productora): '''Ingresas la productora, retornando la ganancia total y la cantidad de peliculas que produjeron''' return {'productora':productora, 'ganancia_total':respuesta, 'cantidad':respuesta}

def retorno(pelicula): '''Ingresas la pelicula, retornando la inversion, la ganancia, el retorno y el año en el que se lanzo''' return {'pelicula':pelicula, 'inversion':respuesta, 'ganacia':respuesta,'retorno':respuesta, 'anio':respuesta}

El código para correr la API dentro de FastAPI se puede visualizar aquí

Análisis exploratorio de datos
A los efectos de poder entender los datos presentados, se realizaron una serie de análisis y estudios sobre las variables del dataset a los efectos de poder encontrar relaciones entre los datos y comprender la relevancia de los mismos. Dentro de los análisis efectuados se encuentran distribuciones de frecuencias de las variables numéricas, identificación de variables categóricas y sus valores, correlación entre variables, análisis temporales y por categoría.

Se destaca que se efectuaron algunas transformaciones diferentes a las realizadas para la sección de Engineering.

Se pueden visualizar las transformaciones y los análisis realizados en el siguiente archivo

Modelo de recomendación - Machine Learning
Para el modelo de recomendación de películas Machine Learning se utilizó como criterio filtrar el dataset para las películas estrenadas a partir de 1970 release_year (por mostrar una gran crecimiento a partir de dicho año) y posteriormente filtros por puntajes obtenidos por las mismas vote_average para concluir seleccionando 10.000 títulos.

Se trabajó uniendo los textos de las columnas overview, genres y production_companies para concatenarlos en un solo campo de modo que el algoritmo pueda trabajar sobre el mismo combined_features. Una vez con el dataframe listo se procedió a construir 2 modelos para efectuar recomendaciones de películas (uno basado en la similitud del coseno y otro basado en el algoritmo de K-Vecinos).

Se pueden visualizar los códigos realizados en el siguiente archivo

Deployment
Para el deploy de la API, se utilizó la plataforma Render. Los datos están listos para ser consumidos y consultados a partir del siguiente link

Link al Deployment

Video
Para consultar sobre los pasos del proceso y una explicación más profunda es posible acceder al siguiente enlace
