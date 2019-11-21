# Proyecto Final - Topicos especiales en Telematica

## Integrantes: 
Juan Pablo González

## Librerias utilizadas:
- NLTK
- Pandas
- TextBlob

### Entendimiento del problema:

Para este problema se cuenta con un dataset de articulos de noticias, con el cual se pretende experimentar por medio de un cluster, apropiandonos de un notebook con soporte a Apache Spark. En mi caso decidí utilizar Databricks Community ya que no tengo suficientes creditos en AWS Educate.

El proposito de este proyecto es aplicar tecnicas de text mining en este dataset, comenzando por preparar y limpiar los datos para así poder aplicar una tecnica de analítica de texto.

### Entendimiento de los datos: 

El dataset proporcionado para este proyecto cuenta con diez columnas, referentes principalmente al titulo del articulo, autor, fecha y lugar de publicación, entre otras. Este cuenta con un total de 50.000 articulos.

En primer lugar, descargué el dataset de la pagina web proporcionada: 
![](https://i.ibb.co/w7dhmjr/s1.png)

Luego procedemos a subir la tabla al Databricks para poder utilizarlo en nuestro notebook: 
![](https://i.ibb.co/VLcs0Wy/s2.png)

Una vez subidos y leidos los datos en el notebook, es necesario limpiar los datos y prepararlos para aplicar text mining. Para limpiarlos debemos cumplir con los siguientes requerimientos:

- *Remover caracteres especiales (. , % ( ) ‘ “ …*
Para esta parte utilicé una funcion simple donde compruebo que cada caracter sea alfanumérico o un espacio. En caso contrario lo descarto.

- *Remover stop-words y palabras de longitud 1*
Aquí utilizo la libreria NLTK (Natural Language Toolkit) la cual me permite tokenizar cada uno de los articulos, para así luego descartar aquellas palabras que son stop-words o de un solo caracter. Esta librería tambien es util para descargar las stopwords del idioma ingles.
En la tokenizacion utilizo la expresion regular (r'\w') la cual me asegura nuevamente que no hayan signos de puntuacion y me separa cada palabra de acuerdo a los espacios en blanco.

- *Radicacion / Lematizacion* 
En este caso he decidido aplicar la lematización, ya que será mas util para el analisis de sentimientos que se realizará. La lematización me permite convertir palabras confugadas en su lema o forma canónica sin ir al extremo de convertir las palabras en raices, ya que las raices pueden resultar en la perdida del significado de la palabra. Para este proceso tambien hago uso de la libreria NLTK por medio de la funcion WordNetLemmatizer

Hice uso de la librería Pandas hasta este momento para leer el archivo .csv, ya que esta me permite modificar valores de las tablas de una forma mas eficiente por medio del metodo _apply()_

### Analisis de sentimiento

Para el analisis de sentimiento realizado utilicé la libreria TextBlob que me facilita por medio de sus funciones un analisis léxico de los textos, y una estimacion de polaridad de cada articulo. En el notebook se puede observar el resultado del analisis de sentimiento en el ultimo dataframe, donde la columna "sentiment" nos indica la polaridad como un numero que va entre el rango [-1.0 , 1.0] siendo -1.0 relacionado con un contenido negativo y 1.0 con uno positivo.

Se debe tener en cuenta que al tratarse de un articulo es muy probable que la polaridad oscile entre [-0.5 , 0.5] o incluso menos, dependiendo del contenido noticioso que contenga, ya que son palabras que no se pueden asociar directamente a un sentimiento positivo o negativo.

### Notebook: 
https://databricks-prod-cloudfront.cloud.databricks.com/public/4027ec902e239c93eaaa8714f173bcfc/7467927995929030/1050917737771856/4772904610073869/latest.html

### Referencias
https://towardsdatascience.com/nlp-for-beginners-cleaning-preprocessing-text-data-ae8e306bef0f
https://textblob.readthedocs.io/en/dev/quickstart.html#sentiment-analysis
