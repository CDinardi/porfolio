[< Inicio](/index.md)

# Reconocimiento de números 

![image](https://user-images.githubusercontent.com/11593599/143690419-de3a89f4-c50e-45a0-ab8e-4312ee57902f.png)

Un problema clásico en el deep learning es el reconocimiento de números dibujados a mano alzada.
Para esto utilizaremos la extensión de RapidMiner llamada Deep Learning en su versión 1.1.2.

Para iniciar verificamos el contenido de los [archivos](https://drive.google.com/drive/folders/13wovnAqprxlWX1ABUrXQgfkNO7qq7eKQ?usp=sharing).
Podemos observar que tiene 785 columnas, la columna label indica el número que representa, y las restantes 784 representan la intensidad de 0 a 1 (0=blanco absoluto, 1=negro absoluto) de cada pixel de la imagen del número, cada imagen es de 28x28 pixel. 

Necesitamos que la columna que indica el valor real del número sea del tipo nominal, para esto vamos a crear una nueva columna y posteriormente la seteamos como label.

![image](https://user-images.githubusercontent.com/11593599/143719831-1a1dd7e5-f7a4-4d6b-96be-4f296a2874bb.png)

Agregamos el bloque Deep Learning desde la seccion de extensiones.

![image](https://user-images.githubusercontent.com/11593599/143719869-4777f636-bb13-4049-8a51-d69a8a7b870f.png)

![image](https://user-images.githubusercontent.com/11593599/143719884-33ddc7b5-440f-4e60-ac75-4f5ca48c8f99.png)

Indicamos el valor 20 en epoch para indicar que el modelo itere esa cantidad de veces el conjuto de datos.

Dentro del bloque Deep Learning es donde construimos las capas de neuronas.
Por tener 784 entradas vamos a agregar un bloque Fully-Connected de 784 neuronas y la función de activación ReLu. Para la salida agregamos otro Fully-Connected pero vamos a seleccionra 10 neuroas de salida, ya que son la cantidad de valores diferentes que tendremos, y por este motivo elegimos la función SoftMax el cual nos dara la probabilidad por cada una de las salidas.

![image](https://user-images.githubusercontent.com/11593599/143718524-134cf6cd-b87e-492c-8f52-11cd81512658.png)

![image](https://user-images.githubusercontent.com/11593599/143718516-fd7d19e7-a978-4f3c-9006-4a04f41024cd.png)

Repetimos el proceso de crear una nueva columna nominal y setearla como label para el set de pruebas. Agregamos un bloque de Apply Model y un bloque de Performance para medir el Accuracy de nuestra red neuronal.

![image](https://user-images.githubusercontent.com/11593599/143718511-78428793-f15a-49aa-a1e3-7dbc90c92d3f.png)

## Resultado
Utilizando las capas descriptas podemos obtener un 94.9% de Accuracy, un número realmente bueno para el problema, pero vamos a validar que sucede agregando una mayor cantidad de capas en nuestra red neural para intentar mejorar su performace.

![image](https://user-images.githubusercontent.com/11593599/143690639-251754a2-3eab-40b1-9c26-927b4055fe6f.png)

#### Resultado con 3 Capas
Agregando un nueva capa de 784 neuronas y función ReLu, obetenemos un Accuracy de 95.5%, una leve mejora. 

![image](https://user-images.githubusercontent.com/11593599/143690677-d3d4dfea-a645-4e88-9be9-851c8e92a3dc.png)
![image](https://user-images.githubusercontent.com/11593599/143716573-2e01508d-966c-47de-b011-b81f3b90abfa.png)


#### Resultado con 4 Capaz
Para intentar mejorar nuestra red agregamos nueva capa, y vemos que sufrimos un sobreentranamiento al intentar complejisar una red innecesariamente.
![image](https://user-images.githubusercontent.com/11593599/143716960-7afe335e-7e87-4fe3-bd10-dd5f97778c40.png)
![image](https://user-images.githubusercontent.com/11593599/143718504-2fc7d137-f532-4b98-8038-e8dbff154acf.png)

#### Modificando la cantidad de iteraciones
En busca de un mejor accurancy de nuestra red neuronal y partiendo del modelo de 3 capas el cual fue la mejor estructura de las probadas, modificamos el valor epoch a 50 de nuestro bloque Deep Learning, este valor señala que la red neuronal iterará 50 veces el conjunto de datos.
El resultado logrado es un 98.8% de Accuracy, al igual que con la cantidad de capas utilizada si aumentamos demasiado la cantidad de iteraciones podemos caer en un sobreentrenamiento que a la mínima diferencia con respecto al set de entrenamiento podría darme un resultado incorrecto.

![image](https://user-images.githubusercontent.com/11593599/143723441-3c79ac30-e666-4d12-b38f-81edddb06496.png)


## Referencias
[https://victorzhou.com/blog/keras-neural-network-tutorial/](https://victorzhou.com/blog/keras-neural-network-tutorial/)

[http://myselph.de/neuralNet.html](http://myselph.de/neuralNet.html)
