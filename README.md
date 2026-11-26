# tarea-investigacion-clustering-pedro
Investigación y Desarrollo sobre Algoritmos de Clustering
Parte 1: Algoritmos No Supervisados de Clustering

1. ¿Qué es el aprendizaje no supervisado y qué es un algoritmo de clustering? ¿En qué se diferencia del aprendizaje supervisado y cuál es su propósito?
   
   El aprendizaje no supervisado es una variante del Machine Learning donde el modelo no aprende recibiendo respuestas correctas de ejemplos. Trabaja sin etiquetas previas, recibe características de elementos y su objetivo es encontrar grupos o estructuras natruales ocultas.
   Propósito: Un algoritmo de clustering divide un conjunto de datos en grupos (o clusters), siendo los integrantes del grupo muy similares y diferentes a los de otros grupos (o clusters)

 
2. Explique la diferencia conceptual entre el clustering basado en centroides (particional) y el clustering jerárquico, mencionando un algoritmo representativo de cada enfoque
   
   El clustering basado en cnetroides divide los datos en un número de grupos (K) alrededor de puntos centrales (denominados centroides). Algoritmo representativo: K-means
   El clustering jerarquico construye una estructura llamada dendrograma, uniendo los puntos más cercanos de manera repetitiva, hasta formar un grupo global. Después se decide en que nivel de ramas se hace el análisis para que sea más adecuado. Algoritmo representativo: Agglomerative Clustering


   
3. ¿En qué consiste el clustering basado en densidad (como DBSCAN) y cómo difiere del basado en centroides y del jerárquico?

   El clustering basado en densidad (como DBSCAN) se fundamenta en el estudio de puntos y agrupación de estos conforme se incluyen en un área definida por un radio (epsilon) con proximidad al punto de estudio. Se detectan así zonas densamente pobladas, que se agrupan y puntos aislados o ruido.

   El enfoque del clustering de DBSCAN es de agrupación en el estudio de los puntos con un perfil radial, pero se van agrupando los puntos cercanos de manera que las formas finales, pueden ser irregulares, curvas, alargadas… en cambio en el enfoque de centroides y jerarquico, la agrupación suele tener perfiles circulares o redondeados.
A nivel de ruido, el clustering basado en densidad,  identifica y aisla a los puntos distantes u outliers. Al contrario que en los dos siguientes donde todos los puntos se suelen asignar a algún grupo.

   El número de clusters no se indica, del mismo modo que en el jerarquico, ya que surgén a través del análisis. En K-means es condicionante de inicio.

   
 
4. ¿Por qué es importante elegir correctamente el número de clusters o los hiperparámetros de un algoritmo de clustering? Explica al menos dos métodos para evaluar la calidad de un agrupamiento (por ejemplo, el método del codo y el coeficiente de silueta)

- La elección de hiperparámetros o cluster puede generar una fragmentación no adecuada de los grupos, crear grupos poco realistas, mezclar categorías o clasificar datos válidos como ruido.
- El método del codo mide la inercia (que es una medición matemática entre el punto seleccionado y el centroide de su grupo) para distintos valores de K (que sería el número óptimo de clusteres a decidir), buscando el punto donde no se aprecian más cambios significativamente, al añadir mas grupos. 
- El coeficiente de la silueta varia entre -1 y +1 y mide como de similar es un punto a su propio grupo  en comparación con el grupo vecino. Si el valor es cercano a 1, los clústeres están bien separados.
Cuando es cercano a cero, los grupos se solapan, y cuando es cercano a -1 algunos puntos podrían ser asignados al cluster equivocado.

   
5. Explica brevemente los siguientes algoritmos:
   (Para cada uno, incluye una breve descripción del mecanismo, ventajas, desventajas y casos de uso comunes.)
   
 - K-means
   -   Descripción: Partimos de un número de clusters (K) que puede venir condicionado por el cliente o negocio. Ubicamos          unos centroides de manera arbitraria inicialmente. Seleccionamos un punto del estudio y medimos la distancia a cada         uno de los centroides. Se asignaré pertenencia al cluster donde tenga el centroide más cercano según distancia              euclídea. Una vez asignados todos los puntos, el siguiente paso es acercar el centroide al centro del cluster               generado, usando el promedio de todos los puntos del cluster. Volvemos a mirar la distancia de todos los puntos a           la nueva posición del centroide y determinamos pertenencia de los puntos a cluster nuevamente. Importante, aparece          un parámetro llamado inercia calculada con la distancia al cuadrado de cada uno de los puntos al centroide, para dar        más peso al punto lejano.
   -   Ventajas: Rápido y escalable a grandes volúmenes de datos
   -   Desventajas: Partir de un K inicial, quizás preestableciod como requerimiento. Funciona bien con grupos de forma            esférica y es sensible a outliers (valores atípicos)
   -   Casos de usos comunes: Segmentación de clientes bancarios (p.e. saldo bancario vs uso tarjeta de crédito),                  campañas de marketing segmentadas, agrupación de documentación.   
     
 - Clustering Jeráquico
   -   Descripción: Inicialmente todos los puntos son clusters, después se van combinando con una función incremental para         crear clusters más grandes. Podemos, como primera base de estudio convertir los puntos en vectores, con análisis de         la función coseno, para ver similitudes entre ellos y hacer una matriz para visualizarlos. Medimos también la               distancia entre vectores mirando distancia  euclidiana (hipotenusa). Inicialmente cada punto era un cluster, a              partir de la medición de la distancia euclidiana, voy uniendo puntos en clusters por proximidad y lo voy                    representando en un dendograma o árbol de decisiones. En el dendograma se verá una jerarquía de clusters.                   Seguidamente cortamos el dendógrama a partir de una distancia que elijamos, y nos quedamos con los clusters creados         por debajo de esa distancia.
   -   Ventajas: No hay un número de clusters fijo al principio. La representación visual es intuitiva y permite la toma de        decisiones de manera más consciente.
   -   Desventajas: Consumo de memoria elevado. Proceso más lento. Las fusiones de clusters realizadas conforme se avanza,         no se pueden deshacer.
   -   Casos de usos comunes: Análisis biológicos, catálogos de despiece de productos.
     
 - DBSCAN
   -   Descripción: DBSCAN (Acrónimo de Density-Based Spatial Clustering of Applications with Noise → Técnica de                   clusterizado espacial basada en densidad para aplicaciones con ruido). Primeramente se selecciona un punto y he de          determinar si se encuentra dentro de una región densa. Para definir lo que es una seccion lo hacemos a trvés de un          parámetro llamado épsilon que se usará como radio de un circulo. Contaremos la cantidad de puntos incluidos dentro          de ese radio. Definimos un umbral, que es una variable numérica a partir de la cual decidimos que es una zona               densamente poblada. Si es asi, podemos decir que ese punto es un punto core y  formará parte de un cluster. Este            procedimiento lo repetimos para todos los puntos. Si el punto no forma parte de una zona densamente poblada, se             considerará ruido y no formará parte de un cluster. Una vez considerada toda la estructura, habrá puntos de contacto        que no se han considerado dentro del cluster por no cumplir con el umbral, pero que son contiguos a áreas densas.           Estos puntos añadidos, no servirán para añadir puntos adicionales, porque ya estaban en una situación delicada.
   - Ventajas: Los grupos pueden ser de formas dispares, no siempre circulares. No es necesario definir el número de               clusters inicial. Fiabilidad considerando outliers.
   - Desventajas: Sensible a las elecciones de épsilon y corte mínimo o umbral. Si los grupos son muy dispares, se piede           eficacia.
   - Casos de usos comunes: Análisis termográfico, Detección de ataques fraudulentos, anomalias de detección en sensores.
     
 - Gaussian Misture Models (GMM)
   - Descripción:
   - Ventajas:
   - Desventajas:
   - Casos de usos comunes:
     
   
   


 
