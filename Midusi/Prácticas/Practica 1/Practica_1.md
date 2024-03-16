# Práctica 1: Preprocesamiento de los datos

### 1. Automóviles

Analice la información del archivo automobile.csv cuyo contenido se encuentra descripto en “automobile_names.txt”
1. Indique qué tipo de gráfica puede construir con los atributos. Ejemplifique cada caso.
2. Utilizando distintas representaciones gráficas, describa la distribución de los atributos, e indique si observa relaciones entre los mismos.
3. La Minería de Datos permite extraer dos tipos de conocimiento: descriptivo y predictivo. Ejemplifíquelos para el caso de los autos.
4. Calcule el coeficiente de correlación lineal entre los atributos numéricos. Relacione los valores obtenidos con los diagramas de dispersión de cada par de atributos.

### Resolución
#### Punto 1

 Hay que tener en cuenta el tipo de variable (categórica, continua). Para las variables **continuas** tales como _normalized-losses_, _wheel-base_, _length_, _height_, etc podría realizar gráficas tales como histogramas, box plots, gráfico de dispersión para explorar relaciones entre pares de variables continuas o mapa de calor para visualizar la correlación entre todas las variables continuas. 

Para las variables **categóricas** tales como _symboling_, _make_, _fuel-type_, etc, se podría realizar gráficos de barra o gráficos de torta.

También se podría realizar gráficas para analizar la relación entre las variables categóricas y continuas, como un diagrama de cajas apiladas por ejemplo, o bien podría realizarse una exploración en general podría realizarse un diagrama de correlación.

**Algunos gráficos de ejemplo**:

![Histograma Normalized-losses](Images/Histograma-Normalized-losses.svg)

![Gráfico de barras variable make](Images/Bar-Make.svg)

![Gráfica de cajas apiladas Price y Fuel-Type](Images/Stacked-Box-Plot-Price-Fuel-Type.svg)

#### Punto 2:
