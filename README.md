# Proyecto Machine Learning 
***Proyecto Individual N°1_Data Science_Henry***

Este proyecto abarca una serie de pasos para desarrollar un proceso de Data Engineering sobre un dataset de videojuegos, para posteriormente disponibilizar una serie de endpoints y un modelo de recomendación de juegos utilizando Machine Learning, a través de una API.

![logo](https://www.datascience-pm.com/wp-content/uploads/2021/06/ml-ops-venn-diagram-600.png)

### Contexto
Se plantea desde los propietarios de la plataforma 'Steam Games' la necesidad de contar con los datos en una API para poder ser consumidos. Por otro lado existe la necesidad de poder realizar las consultas al modelo de recomendación para lo cual resulta necesario hacer un deploy de la API.

### Dataset
Son tres (3) dataset que poseen información acerca de juegos, reseñas y distintos atributos de los mismas, en formato JSON. Los mismos se adjuntan el el [siguiente enlace](https://drive.google.com/drive/folders/1r0yc_x2rVsMoTVIUFw3W3Zh0UaXi7wvF?usp=drive_link), ya que por su tamaño no pudieron ser agregados al presente repositorio. 


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
* Se guardaron esos dataset en tres diferentes archivos formato CSV. [Games.csv]. [Reviews.csv]. El archivo Items.csv no pudo ser agregado al repositorio por su tamaño. Para acceder al mismo, siga el [siguiente link](https://drive.google.com/file/d/1sSZjSbrGfwv7JrilfZfdxcFbyO_rYuJy/view?usp=sharing)
* Posteriormente se unieron los tres dataset en uno solo, eliminando nuevamente datos duplicados, o innecesarios para el análisis.
* Se guardó la información obtenida en el archivo Total.csv.
  

### API
Se solicitó efectuar la disponibilización de los siguientes endpoints a través del Framework ***FastAPI***:

* def PlayTimeGenre(genero:str): Crear una función con la que se obtiene el año de lanzamiento con más horas jugadas para un género dado. Ejemplo: {"Año de lanzamiento con más horas jugadas para [genero]": [año]}

* def UserForGenre(genero: str): Crear una función con la que se obtiene el usuario con más horas jugadas y la acumulación de las mismas por año, para un género dado. Ejemplo: {"Usuario con más horas jugadas para [genero]": [usuario]} "Acumulación de horas jugadas por año para [genero]": [año: horas]
  
* def UsersRecommend(anio: int): Crear una función que devuelva el top 3 de juegos MÁS recomendados por usuarios para el año dado. Ejemplo: {"Puesto 1": 'nombre de juego', "Puesto 2": 'nombre de juego', "Puesto 3": 'nombre de juego'}

* def UsersNoRecommend(anio: int): Crear una función que devuelva el top 3 de juegos MENOS recomendados por usuarios para el año dado. Ejemplo: {"Puesto 1": 'nombre de juego', "Puesto 2": 'nombre de juego', "Puesto 3": 'nombre de juego'}

* def sentiment_analysis(anio:int):Crear una función que según el año de lanzamiento, se devuelve una lista con la cantidad de registros de reseñas de usuarios que se encuentren categorizados con un análisis de sentimiento. Ejemplo: {Negative = [cantidad_reseñas], Neutral = [cantidad_reseñas], Positive = [cantidad_reseñas]}

El código de éstas funciones se puede visualizar en el [siguiente archivo](https://github.com/ACGomezW/Proyecto_Machine_Learning/blob/main/ParaFunciones.ipynb))


### Modelo de recomendación - Machine Learning
Para el modelo de recomendación de juegos Machine Learning se utilizó una muestra aleatoria de los datos de preferencias de usuarios, utilizando el método 'similitud de coseno' con una matriz de 50 x 50, obteniendo con una función los juegos recomendados al usuario, según sus preferencias anteriores.  

Se pueden visualizar los códigos realizados en el [siguiente archivo](https://github.com/ACGomezW/Proyecto_Machine_Learning/blob/main/ParaML.ipynb)

### Deployment
Para el deploy de la API, se utilizó la plataforma Render. Los datos están listos para ser consumidos y consultados a partir del siguiente [link](https://api-pi1.onrender.com)


### Video
Para consultar sobre los pasos del proceso y una explicación más profunda es posible acceder al [siguiente enlace](https://www.youtube.com/watch?v=rZvtQSl0xxE&t=121s)
