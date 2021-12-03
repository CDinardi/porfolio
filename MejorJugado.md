# Mejor jugador del partido

A partir de los datos del mundial 2018 se busca armar un arbol de decisión del equipo que tuvo al mejor jugador del partido. [Archivo](https://drive.google.com/file/d/1h2CfKcx9kMQWAS5uhjf4RAO04j-NBjVy/view?usp=sharing)

Para esto inicialmente cargamos el archivo, seteamos el campo Man of the Match como campo label ya que es el relevante para este problema, y para evitar errores en la creación del arbol indicamos que Team y Oponent son del tipo ID, para que no interfieran en el futuro árbol.

![image](https://user-images.githubusercontent.com/11593599/144561369-c67e6102-1729-4a3c-948c-e7f73acfd294.png)

![image](https://user-images.githubusercontent.com/11593599/144561406-e2682bb3-a0c6-4287-91f2-100911bec401.png)

![image](https://user-images.githubusercontent.com/11593599/144561434-97b39076-da8c-4f94-b20d-27fee96ac6b4.png)

Agregamos un bloque Cross Validation, el cual separará el set de datos en un subgrupo para training y otro para pruebas.

![image](https://user-images.githubusercontent.com/11593599/144561554-f07e5a89-be28-4dab-bc16-303a78b56b99.png)

Dentro del bloque Cross Validation y en la sección de Training vamos a agregar el bloque de Decision Tree.

![image](https://user-images.githubusercontent.com/11593599/144561614-c945dfa8-84e6-4bb8-85fa-20378bc5894a.png)

En la sección de Test agregamos un bloque Apply Model donde utilizaremos el modelo del Árbol de Decision creado con el set de test, y un bloque de Performance (Classification) para medir que tan bueno fue nuestro Árbol respecto a los datos reales.

![image](https://user-images.githubusercontent.com/11593599/144561774-7fea6122-ba94-4fe0-a97d-8215c7e4abcd.png)

#### Resultados

Matriz de Confusión

![image](https://user-images.githubusercontent.com/11593599/144561831-9cd67980-0006-428a-9157-21846473329c.png)

### Conclusiones

Se creó un Árbol de decisión para el jugador del partido, dicho modelo tiene un accuracy de 73%.
Tal como vemos en la matriz de confución los equipos identificados por nuestro modelo como el equipo que tiene al Jugador del Partido y que realmente lo tienen, cumple con un acierto de 85.94%. Sin embargo el cuando el modelo indica que un equipo no tiene al jugador del partido solo se acertó un 60.94%.
El set de datos se encuentra nivelado, por lo tanto la diferencia de porcentajes no está relacionado a la calidad de los datos. Esto quiere decir que a pesar de que el accuracy de nuestro modelo no es bajo existe un margen de mejora principalmente para mejorar la cantidad de Falsos Positivos.

#### Referencia
https://www.kaggle.com/mathan/fifa-2018-match-statistics
