# Proyecto Indiviual 1: Sistema de recomendacion de peliculas

![image](https://github.com/user-attachments/assets/de28fa21-e50b-4749-abfc-04273505e982)


# Introducion

El objetivo del presente proyecto es simular un ambiente de trabajo donde cumplimos el rol de **Data Scientist** dentro de una start-up que provee servicios de agregación de plataformas de streaming.
La misma nos solicita construir un modelo de Machine Learning(ML) que ponga en marcha un sistema de recomendacion de peliculas totalmente nuevo.
Para lograr este objetivo debemos combinar un trabajo de **Data Engineer** que posteriormente nos permita construir un **Producto Viable Minimo(MVP)** de un sistema de recomendacion de peliculas.

*Recordemos que el **MVP** es una metodología de desarrollo de productos o servicios que se centra en crear un producto con el mínimo conjunto de características necesarias para validar 
su viabilidad en el mercado y obtener retroalimentación de los usuarios lo antes posible. 
La idea detrás de este procedimiento es lanzar algo lo suficientemente funcional como para que los usuarios puedan interactuar con él y proporcionar comentarios y datos de uso, pero sin gastar recursos excesivos en el desarrollo de características complejas que pueden no ser necesarias o relevantes para los usuarios.*

Para llevar adelante esta tarea utilizaremos las siguientes herramientas:
* **Visual Studio Code(VS Code):** es un editor de código fuente ligero, multiplataforma y altamente personalizable, desarrollado por Microsoft. Es popular entre desarrolladores debido a sus características avanzadas, como la depuración integrada, el control de versiones (Git), la finalización de código inteligente, y su amplia gama de extensiones que permiten soporte para múltiples lenguajes de programación y herramientas de desarrollo. Además, es gratuito y de código abierto.

* **Fast Api:** es un framework web moderno y de alto rendimiento para construir APIs en Python. Es conocido por su rapidez y eficiencia, tanto en términos de tiempo de desarrollo como en rendimiento. FastAPI utiliza tipado basado en anotaciones de Python para generar automáticamente la documentación de la API (como OpenAPI y Swagger UI), lo que facilita el desarrollo y la comprensión del código. También es compatible con la asincronía, lo que lo hace ideal para aplicaciones que requieren manejar múltiples solicitudes simultáneamente de manera eficiente. Es ampliamente utilizado para crear APIs RESTful y microservicios.

* **Render:** es una plataforma de alojamiento en la nube que permite desplegar aplicaciones web, APIs, bases de datos y otros servicios de manera sencilla y escalable.

## Tabla de contenidos
- [Introducción](#introducción)


## ETL

(Extract, Transform, Load) es un proceso en la gestión de datos que implica tres etapas clave:
-*Extract (Extracción)*: Se extraen datos de diferentes fuentes, como bases de datos, archivos, APIs, etc.
En este caso trabajamos con documentos CSV que se pueden descargar aqui:
- + [Dataset](https://drive.google.com/drive/folders/1X_LdCoGTHJDbD28_dJTxaD4fVuQC9Wt5?usp=drive_link)

-*Transform (Transformación)*: Los datos extraídos se limpian, se transforman y se estructuran para cumplir con los requisitos de negocio o de almacenamiento.
Para esto utilizaremos principalmente la biblioteca [Pandas](https://pandas.pydata.org/docs/user_guide/10min.html) que nos facilita el trabajo con CSVs.

-*Load (Carga)*: Los datos transformados se cargan en un sistema de destino, como un data warehouse, base de datos, o cualquier sistema de almacenamiento de datos.
En este caso, ambos datasets fueron unificados y llevados al archivo **'2.base_de_datos'**

El proceso ETL es fundamental para integrar datos de múltiples fuentes en un repositorio central, facilitando análisis, reportes y toma de decisiones basadas en datos.

## Fast Api
Ahora, utilizando *Fast Api*, vamos a disponibilizar los datos de la empresa a los usuarios para que puedan ser testeadas las operaciones deseadas.
Para ello desarrollamos seis funciones que demuestren ser eficaces.

Se pueden observar en el apartado de **funciones.py:**
+ def **cantidad_filmaciones_mes(*`Mes*`)**: Se ingresa un mes en idioma Español. Debe devolver la cantidad de películas que fueron estrenadas en el mes consultado en la totalidad del dataset.

+ def **cantidad_filmaciones_dia( *`Dia`* )**: Se ingresa un día en idioma Español. Debe devolver la cantidad de películas que fueron estrenadas en día consultado en la totalidad del dataset.

+ def **score_titulo( *`titulo_de_la_filmación`* )**: Se ingresa el título de una filmación esperando como respuesta el título, el año de estreno y el score.

+ def **votos_titulo( *`titulo_de_la_filmación`* )**: Se ingresa el título de una filmación esperando como respuesta el título, la cantidad de votos y el valor promedio de las votaciones. La misma variable deberá de contar con al menos 2000 valoraciones, caso contrario, debemos contar con un mensaje avisando que no cumple esta condición y que por ende, no se devuelve ningun valor.

+ def **get_actor( *`nombre_actor`* )**: Se ingresa el nombre de un actor que se encuentre dentro de un dataset debiendo devolver el éxito del mismo medido a través del retorno. Además, la cantidad de películas que en las que ha participado y el promedio de retorno. **La definición no deberá considerar directores.**

+ def **get_director( *`nombre_director`* )**: Se ingresa el nombre de un director que se encuentre dentro de un dataset debiendo devolver el éxito del mismo medido a través del retorno. Además, deberá devolver el nombre de cada película con la fecha de lanzamiento, retorno individual, costo y ganancia de la misma.

## EDA
(Exploratory Data Analysis) Es un proceso en el análisis de datos que implica explorar y analizar datasets para descubrir patrones, detectar anomalías, probar hipótesis y resumir las principales características. Se utilizan estadísticas descriptivas y visualizaciones para entender mejor los datos antes de aplicar modelos más avanzados o tomar decisiones.

En este caso la idea principal fue identificar las posibles relaciones entre variables y la deteccion de outliers.
Algunos ejemplos:

**Matriz de correlacion**

*Es una tabla que muestra los coeficientes de correlación entre varias variables en un dataset. Estos coeficientes indican la fuerza y dirección de la relación entre dos variables, con valores que van de -1 (correlación negativa perfecta) a 1 (correlación positiva perfecta), y 0 indicando ninguna correlación. Es útil para identificar relaciones entre variables.*

![image](https://github.com/user-attachments/assets/6a0994d9-8538-43a3-a8a8-2d892fb9d647)




