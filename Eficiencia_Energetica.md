# Eficiencia Energética

El objetivo de esta practica es hallar los coeficientes para lograr predecir a travez de regresión lineal la eficiencia energética de un edificio a partir de algunos valores de su estrucuta tales como el Área de superficie, muros, techo, orientación, vidrios, entre otros.
[Archivo](https://drive.google.com/file/d/1Qp9i43d7SlBwMF68G8mhkX8B0pau_phz/view?usp=sharing)

En primer lugar corroboramos si existen faltantes de datos.
![image](https://user-images.githubusercontent.com/11593599/144550474-3aa3f070-24fe-4c11-b8c1-66e3ba389166.png)

Posteriormente indicamos cual será el campo que queremos predecir.
![image](https://user-images.githubusercontent.com/11593599/144550542-490091fc-9658-4180-8cf2-afe12532cc7a.png)
![image](https://user-images.githubusercontent.com/11593599/144550563-8bea1cc1-dea5-4944-9322-84bfbdccaab6.png)

Agregamos el bloque Cross Validation, el cual dividirá el set de datos en traning donde nos brindará un modelo y testing que posteriormente vamos a calcular su performance.
![image](https://user-images.githubusercontent.com/11593599/144550692-90b76daa-a0e8-409c-96c6-635c987723af.png)

En la sección de Training agregamos el bloque Linear Regression y conectamos la entrada de datos y la salida del modelo.
![image](https://user-images.githubusercontent.com/11593599/144550751-7538e4ac-3750-433d-9cda-03489faa4b8f.png)

En la sección de Testing agregamos un bloque Apply Model y conectamos la entrada del modelo y el set de Test.
Agregamos un bloque de Performance(Regression) donde le conectamos la salida del Apply model como entrada e indicaremos que nos devuelva la metrica root mean squared error (raix del error cuadratico medio) que nos indica la diferencia entre el valor real y el predicho, y marcamos también la métrica squared correlation (correlacion cuadrática) que es la correlacion entre el valor real y el valor pronosticado elevado al cuadrado.
![image](https://user-images.githubusercontent.com/11593599/144550885-4d56f727-aca6-46cf-b747-fbaff6f92705.png)
![image](https://user-images.githubusercontent.com/11593599/144551394-0c19a655-8368-44c6-bba7-532a5a1ab92d.png)

### Resultados
#### Coeficientes de la regresión
![image](https://user-images.githubusercontent.com/11593599/144552411-441eddf5-cb0d-4b55-93a5-e9c04e45d302.png)

#### Raiz del error cuadrático medio
![image](https://user-images.githubusercontent.com/11593599/144552322-bc1dfcc1-f9dd-4622-858c-a4ab3570b79a.png)

#### Correlacion Cuadrática
![image](https://user-images.githubusercontent.com/11593599/144552346-65041e4c-b90c-45bd-80f2-d827f31909b0.png)

### Conclusión
Mientras más cerca del 0 se encuentra el valor de la raiz cuadrada del error cuadrático medio más perfecta el la predicción, en este caso tenemos un valor bastante bueno.
De la misma forma mientras más se acerque al valor 1 la correlación cuadrática mejor fue nuestra predicción con el modelo conseguido, en este caso nos encontramos en un 0.91, un valor que demuestra que nuestro modelo se acerca realmente mucho a los valores reales.

### Referencia
https://www.kaggle.com/elikplim/eergy-efficiency-dataset
