## Introducción

Este trabajo busca demostrar de manera evidente, mediante una implementación básica cómo es que se pueden explotar las más recientes características de los equipos de cómputo para lograr un procesamiento más veloz, para esto hemos decidido implementar una multiplicación de matrices de manera paralela y secuencial para poder medir los rendimientos y compararlos.

La idea es utilizar distintas herramientas como lo son: contenedores de Docker, maquinas en AWS y programación en paralelo para ejemplificar de manera práctica las mejoras en los tiempos de ejecución que se pueden tener hoy en día.

## Motivación
En los últimos años la velocidad de procesamiento ha crecido debido al uso de procesadores multi-core. Derivado de lo anterior se ha ido teniendo la creciente necesidad de modificar el código de los algoritmos que se usaban comúnmente para adaptarlos de la mejor manera a un paradigma distinto el cual representa una mayor eficiencia, dicho paradigma se le conoce como “procesamiento en paralelo”.

Existen distintas maneras de atacar el problema de paralelizar códigos secuenciales, sin embargo dada la formación de los autores de este trabajo, la manera más natural nos resultó aquella en la cual un grupo de ejecuciones que forman parte de uno o más ciclos “for” se ejecutan cada una en un procesador a manera de que posteriormente podamos reagrupar y obtener el resultado final esperado.

## Pseudo-algoritmo
El resultado final esperado es reducir el tiempo necesario que toma ejecutar un algoritmo mediante una asignación de tareas a los procesadores más eficiente.

Supongamos por ejemplo que deseamos realizar una suma de dos vectores **w = x + y**; con **x, y** en **R**^n

![Imagen1](https://github.com/patricio-hdz/ProyectoFinal/blob/master/Imagenes/Im1.JPG)

En este caso podemos ver como las sumas se podrían realizar de manera simultánea, si asignamos cada pedazo de la suma global a distintos procesadores. Un punto relevante en este caso es que no existen una dependencia entre los procesos que se realizan en cada procesador, por ejemplo esto NO funcionaría si estuviéramos utilizando en cada operación el resultado de la operación anterior, ya que sería necesario forzosamente esperar a tener dicho resultado para poder continuar con las operaciones hasta llegar al resultado final.

Por otro lado una operación NO tan directa es el producto punto de dos vectores **a =< x + y>**; con **x, y** en **R^n** y *a* es un escalar:

![Imagen2](https://github.com/patricio-hdz/ProyectoFinal/blob/master/Imagenes/Im2.JPG)

En este caso es menos evidente la manera en que tendríamos que repartir las operaciones a realizarse en los procesadores, sin embargo se puede realizar de la siguiente manera:

![Imagen3](https://github.com/patricio-hdz/ProyectoFinal/blob/master/Imagenes/Im3.JPG)

De esta manera se logra el objetivo que se tenía y funciona como una buena explicación base para introducir que de esta misma manera, atacamos el problema de paralelizar la multiplicación de matrices ya que en ese caso realizamos esta operación de producto punto entre vectores una y otra vez, pero al no depender una de otra podemos de igual manera "romper" las ejecuciones y paralelizar los procesos.

Medidas control

Ahora presentaremos algunas medidas de control que utilizaremos para evaluar si nuestra implementación está teniendo mejores resultados que una ejecución secuencial; las medidas que usaremos son:

- *Tiempo real de procesamiento*: 
- *Tiempo ideal de procesamiento*:
- *Eficiencia*:

