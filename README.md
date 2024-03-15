Este proyecto abarca una serie de pasos para desarrollar un proceso de Data Engineering sobre un dataset de películas, para posteriormente disponibilizar una serie de endpoints y un modelo de recomendación de películas utilizando Machine Learning, a través de una API.

Contexto:

Se plantea desde los depártamentos de Machine Learning y Analytics la necesidad de contar con los datos en una API para poder ser consumidos. Por otro lado existe la necesidad de poder realizar las consultas al modelo de recomendación para lo cual resulta necesario hacer un deploy de la API.

Dataset:

El dataset (https://drive.google.com/file/d/1_G3BeX4DI46K7FiiypV4j04oIaI7iLf_/view?usp=sharing) en cuestión posee información acerca de películas y distintos atributos de las mismas. El mismo cuenta con 45466 filas (representando cada fila una película) y 24 columnas (atributos de cada título). 

Data Engineering:

Para el trabajo de Data Engineering se procedió a efectuar una serie de transformaciones solicitadas sobre los datos, dentro de las cuales se encuentran:

Algunos campos, como belongs_to_collection, production_companies y otros están anidados, deberás desanidarlos para poder y unirlos al dataset de nuevo hacer alguna de las consultas de la API.

Los valores nulos de los campos revenue, budget deben ser rellenados por el número 0.

Los valores nulos del campo release date deben eliminarse.

De haber fechas, deberán tener el formato AAAA-mm-dd, además deberás crear la columna release_year donde extraerás el año de la fecha de estreno.
Crear la columna con el retorno de inversión, llamada return con los campos revenue y budget, dividiendo estas dos últimas revenue / budget, cuando no hay datos disponibles para calcularlo, deberá tomar el valor 0.

Eliminar las columnas que no serán utilizadas, video,imdb_id,adult,original_title,vote_count,poster_path y homepage.

Se pueden visualizar las transformaciones y los análisis realizados en el siguiente archivo XXXXXXXXXX

API: 

Se solicitó efectuar la disponibilización de los siguientes endpoints a través del Framework FastAPI:

  def peliculas_mes(mes): '''Se ingresa el mes y la funcion retorna la cantidad de peliculas que se estrenaron ese mes (nombre del mes, en str, ejemplo 'enero') historicamente''' return {'mes':mes, 'cantidad':respuesta}

  def peliculas_dia(dia): '''Se ingresa el dia y la funcion retorna la cantidad de peliculas que se estrenaron ese dia (de la semana, en str, ejemplo 'lunes') historicamente''' return {'dia':dia, 'cantidad':respuesta}

  def franquicia(franquicia): '''Se ingresa la franquicia, retornando la cantidad de peliculas, ganancia total y promedio''' return {'franquicia':franquicia, 'cantidad':respuesta, 'ganancia_total':respuesta, 'ganancia_promedio':respuesta}

  def peliculas_pais(pais): '''Ingresas el pais, retornando la cantidad de peliculas producidas en el mismo''' return {'pais':pais, 'cantidad':respuesta}

  def productoras(productora): '''Ingresas la productora, retornando la ganancia total y la cantidad de peliculas que produjeron''' return {'productora':productora, 'ganancia_total':respuesta, 'cantidad':respuesta}

  def retorno(pelicula): '''Ingresas la pelicula, retornando la inversion, la ganancia, el retorno y el año en el que se lanzo''' return {'pelicula':pelicula, 'inversion':respuesta, 'ganacia':respuesta,'retorno':respuesta, 'anio':respuesta}

El código para correr la API dentro de FastAPI se puede visualizar aqui: 

