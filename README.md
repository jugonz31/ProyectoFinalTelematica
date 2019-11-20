# Proyecto Final - Topicos especiales en Telematica

## Integrantes: 
> Juan Pablo González

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
- Remover caracteres especiales (. , % ( ) ‘ “ ….
- Remover stop-words
- Remover palabras de longitud 1
- Stemming / lemmatization
