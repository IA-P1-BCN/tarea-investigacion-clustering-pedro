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
 - K-means
 - Clustering Jeráquico
 - DBSCAN
 - Gaussian Misture Models (GMM)
   Para cada uno, incluye una breve descripción del mecanismo, ventajas, desventajas y casos de uso comunes.
   


 
