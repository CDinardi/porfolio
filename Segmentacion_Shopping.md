# Segmentación de clientes de centro comercial.

### Contexto
Este conjunto de datos se crea solo con el propósito de aprender los conceptos de segmentación de clientes, también conocido como análisis de la canasta de mercado. Demostraré esto usando la técnica ML sin supervisión (algoritmo de agrupamiento de KMeans) en la forma más simple.

### Contenido
Tiene un centro comercial de supermercado y, a través de las tarjetas de membresía, tiene algunos datos básicos sobre sus clientes, como ID de cliente, edad, sexo, ingresos anuales y puntaje de gastos.
El puntaje de gasto es algo que le asigna al cliente en función de sus parámetros definidos, como el comportamiento del cliente y los datos de compra.
[Archivo](https://drive.google.com/file/d/1S-DC2bJ7dfkwDNt1hLcAMYXaTEmXl34s/view?usp=sharing).

### Planteamiento del problema
El propietario del centro comercial desea comprender los grupos de clientes existentes para que el equipo de marketing pueda planificar la estrategia necesaria según el grupo de clientes objetivo.

### Objetivos
Demostrar cómo lograr la segmentación de clientes de un centro comercial mediante el algoritmo de aprendizaje automático (Clustering KMeans) en Python y RapidMiner de forma sencilla.

### Desarrollo

Al iniciar la resolución del problema realizamos un análisis exploratorio en el archivo y nos encontramos con algunos detalles que debemos atender.
![image](https://user-images.githubusercontent.com/11593599/143302583-1e205027-f48f-4486-9ce4-7a2a924af91d.png)
![image](https://user-images.githubusercontent.com/11593599/143305184-7f995601-7942-468e-b8c0-981af90a4a64.png)

En primer lugar podemos ver que la columna género es de tipo texto, por lo cual debemos codificarlo para poder procesarlo, por este motivo se realiza el mapeo de Male = 0 y Female = 1. También existe la columna CustomerID la cual no tiene relevancia para la resolucion de este problema por lo tanto procedemos a quitarla del análisis.
No se encuentra datos faltantes por lo cual podemos continuar con el desarrollo del problema.

Para continuar debemos definir por cuales atributos que queremos agrupar, ya el problema es para el departamento de Marketing podemos encontrar 3 grupos que pueden servir:
     - Puntaje de gastos - Ingresos Anuales, este grupo nos permite identificar las personas que más gastan en el centro comercial agrupada por ingresos, pudiendo hacer una campaña para aquellos que más gastan y tienen ingresos anuales elevados, por lo cual pudieran estár interesados en articulos premium. O atraer la atención de aquellos compradores que tienen altos ingresos pero no gastan mucho, pudiendo existir allí una falta de articulos que llamen su interes.
     - Puntaje de gastos - Edad, estos grupos nos permite por ejemplo identificar la edad de quienes más gastan para promover algún beneficio de su interes y así fomentar un crecimiento en sus compras.
     - Ingresos Anuales - Edad, con estos grupos podemosidentificar los compradores según sus ingresos y edad, pudiendo así realizar campañas de marketing para atraer a los grupos que más ganan por ejemplo brindando sorteos donde el premio se adecúe a la edad de los mismos.
     
Posteriormente realizamos la clusterización variando el parámetro k (cantidad de clusters) para visualizar cual es la segmentación que nos sirve para solucionar el problema. Seguramente para cada uno de los diferentes grupos que decidimos segmentar tendremos una cantidad de clusters diferente, e incluso podría suceder que no existe una cantidad perfecta de clusters sino que podremos tener en la vista gráfica algunos puntos de colores que estan mezclados con otros.

[Código python](https://colab.research.google.com/drive/1uw2Sqm3Y1008YuP_Thd4WwHbqHz_22dJ?usp=sharing).

#### RapidMiner
![image](https://user-images.githubusercontent.com/11593599/143308484-72a5b97c-6242-47a1-91dd-e346273918f1.png)

### Variación de K

#### K=1
Realizar la prueba para K=1 no tiene valor significativo ya que un único grupo es lo que se tiene al leer todo el archivo.

#### K=2
En el caso de K=2 no parecería resolver ninguno de los problemas, por ejemplo vemos que en la primer gráfica existen entre 40 y 60 de Annual Income un grupo que parece bastatente uniforme y sin embargo en la gráfica podemos ver como está agrupando en 2 cluster que están bastante entreverados
![image](https://user-images.githubusercontent.com/11593599/143308571-723da57a-41ff-4471-9cff-ed9cceb35e9f.png)

#### K=3
El caso de K=3 tampoco satisface las necesidades, vemos como por ejemplo en la segunda gráfica vemos que los clientes graficados en color rojo abarcan un rango de puntaje muy amplio e incluso mezclandose  en la parte de puntajes menores a 40.
![image](https://user-images.githubusercontent.com/11593599/143308769-f756afa2-a032-4d0a-b95c-80dff92e2f98.png)

#### K=4
Vemos que con K=4 tampoco satisface ninguna de los casos planteados, por ejemplo en la gráfica de Score-Annual Income el grupo amarillo pudiese dividirse en 2 para mejorar la segmentación
![image](https://user-images.githubusercontent.com/11593599/143311103-c3f33d8b-6cc9-4c86-abac-0babe8a250d5.png)

#### K=5
Cuando probamos con K=5 vemos que la segmentación de la primer gráfica parece bastante suficiente.
![image](https://user-images.githubusercontent.com/11593599/143311595-c2900ca7-9a73-4f7a-9547-8657987465aa.png)

#### K=6
Llegando al K=6 vemos que para el caso de clientes por Score-Age tras aumentar la cantidad de cluster si bien no está haciendo una segmentación perfecta ya que en el caso de clientes con socre menor a 40 vemos que existen 2 cluster muy entreverados, pero si derivamos a marketing que utiliza el grupo rojo y celeste juntos, podemos definir que esta solucion puede satisfacer la necesidad del caso. 
En la gráfica de Annual Income-Age, si bien los cluster logrados no son perfectos, podemos identificar claramente al grupo de 30 a 40 años con ingreso por más de 70 (verde), los clientes menoes a 40 tanto los que tienen ingreso entre 40 y 70 (azul) como los que tienen por ingresos por menos de 40 (anaranjado), también al grupo mayor de 40 años e ingresos entre 40 y 70 (azul claro), pero encontramos el problema del celeste y rojo los cuales tienen algunos puntos entreverados con otros cluster. Una posible decisión en este caso sería agregar el celeste a las campañas del verde para cubrir mayor cantidad de clientes que están entorno al grupo verde. Y en el caso del grupo rojo se puede tomar como un grupo independiente ya que en su mayoria tiene más de 35años y un ingreso anual menor a 40, aunque existen algún caso en los que figuran comprados jovenes, de menos de 20 años y 10 de ingreso, 
![image](https://user-images.githubusercontent.com/11593599/143311698-9d894a7a-4cc3-4f42-af1d-5e4295b48ebb.png)

### Conclusión
Hemos finalizado el desarrollo y resolución del problema planteado llegando a los grupos para entregar al departamente de marketing y de allí puedan generar las campañas adecuadas. Demostramos que se puede utilizar de forma sencilla Kmeans para generar cluster tanto en código Python como en la herramiento Rapidminer, y ambas me permiten visualizar los datos facilmente para poder interpretar mejor las soluciones.

[Referencia](https://www.kaggle.com/vjchoudhary7/customer-segmentation-tutorial-in-python).
