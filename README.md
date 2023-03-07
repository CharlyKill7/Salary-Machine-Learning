# W7 Project - Salary: Machine Learning

![portada](https://github.com/CharlyKill7/Salary-Machine-Learning/blob/main/img/money.png)

## Índice

1. [Descripción](#descripción)
2. [Transformación](#transformacion)
3. [Encoding](#encoding)
4. [Models](#models)
5. [Conclusiones](#conclusion)


<a name="descripción"/>

## Descripción del proyecto

Este proyecto es una competición de Kaggle, donde habrá que utilizar Machine Learning para predecir el salario dentro del sector Data, a partir de unos .csv que contienen datos como el puesto, el país de residencia o el tipo de contrato, entre otros. 

### Restricciones:
- No está permitido eliminar filas en los datos de testeo o prueba.

### Dataset:
- <em>salaries_data.csv</em>: contiene el conjunto de datos de entrenamiento.
- <em>testeo.csv</em>: contiene el conjunto de datos de prueba.
- <em>muestra.csv</em>: ejemplo de formato de la predicción para su carga en Kaggle.

### Objetivo:
 
Nuestro objetivo será aplicar y mejorar modelos de Machine Learning, probando varias transformaciones, encodings, hiperparámetros y modelos, con el fin de obtener el menos RMSE que sea posible.

 
 <a name="transformacion"/>
 
## Tranformación

Logicamente, lo primero fue realizar un análisis exploratorio de los datos, comprobando los valores nulos, el tipo de objeto de cada columna, las dimensiones del Dataframe, etc. Este proceso se llevó a cabo en el notebook 'draft', aunque muchas de las pruebas fueron borradas sobre la marcha. También se unificó en una sola columna el salario, quedándonos con salary_in_usd y renombrándola.

Tras esto, tomamos la precaución de comprobar si había valores en los datos de prueba que no estuvieran en el entrenamiento. Descubrimos así tres columnas con valores distintos: employee_residence, company_location y job_title.

<br>
<br>

<img src="https://github.com/CharlyKill7/Salary-Machine-Learning/blob/main/img/tra_1.png" />

<br>
<br>

Decidimos tratar estos valores uno a uno, procurando dar todo el sentido posible a los datos. En el caso de job_title, en 'draft' hicimos unas cuantas pruebas, buscando los puestos más similares en el resto de columnas y asignando el job_title más oportuno en cada caso. Por otro lado, para las otras dos columnas, buscamos en internet los paises más parecidos en cuanto a salarios para el sector IT/Data, y sustituimos en consecuencia por el caso más adecuado de cuantos están en los datos de entrenamiento.

<br>
<br>

<img src="https://github.com/CharlyKill7/Salary-Machine-Learning/blob/main/img/tra_1.png" />

<br>
<br>

Hasta aquí el proceso de transformación "clásica".

 <a name="encoding"/>
 
## Encoding

¿Pase o Carrera? Esa es la gran pregunta a la que se enfrenta un entrenador antes de cada jugada. En pocas palabras, pasar significa lanzar por aire, arriesgando más el balón con vistas a obtener un beneficio mayor en cuanto a yardas. "Carrera", por el contrario, es una forma segura de avanzar desde atrás, aunque las yardas recorridas suelen ser muchas menos. 

En el siguiente dashboard podemos apreciar, de manera general, lo que voy a ir destripando por secciones.

<img src="https://github.com/CharlyKill7/NFL-Success_Visualization/blob/main/images/pass_vs_rush.png" />

<details>
<summary>Score & Passing</summary>
<br>

 ![pass](https://github.com/CharlyKill7/NFL-Success_Visualization/blob/main/images/pass_scatter.png)
	
En este "scatter plot", o mapa de puntos, podemos apreciar que a mayor número de intentos de pase, mayor número de puntos en el marcador. A grandes rasgos, existe una correlación directa entre el número de intentos de pase y los puntos, salvo alguna excepción como Cleveland Browns. 

</details>

<details>
<summary>Score & Rushing</summary>
<br>

 ![rush](https://github.com/CharlyKill7/NFL-Success_Visualization/blob/main/images/rush_scatter.png)
	
Por contra, en este otro mapa podemos observar que un mayor nº de jugadas de carrera no necesariamente se ve traducido en más puntos. Cabe destacar que, como ya intuimos, New England Patriots es líder en no importa qué tipo de jugada. Hay no obstante otros casos sumamente interesantes, como el de New Orleans Saints. Pasan de estar en el top 2 de intentos de pase a estar por debajo de la media de la liga en carrera, siendo terceros globales en anotación. Esto ya da una pista de por dónde van los tiros.

</details>

<details>
<summary>Top & Bottom Teams Play Distribution</summary>
<br>

![top](https://github.com/CharlyKill7/NFL-Success_Visualization/blob/main/images/top_pass_rush.png)
![bot](https://github.com/CharlyKill7/NFL-Success_Visualization/blob/main/images/worst_pass_rush.png)
	
En efecto, estas dos tablas resultan esclarecedoras. Teniendo en cuenta sólo los partidos que terminaron en victoria, podemos apreciar que la distribución de jugadas es distinta para los equipos Top y los peores de la liga. Los mejores pasan más, mientras que los peores optan por la carrera como el vehículo principal de su victoria.

</details>
<br>

<a name="qb"/>

## QB Dependency

De acuerdo, parece más efectivo pasar que correr. Sin embargo, la probabilidad de completar un pase no es la misma en todos los equipos. Sin explayarme, para que un pase tenga éxito, hay varias posiciones del juego involucradas. Un quarterback que lanza, un receptor que corre a atraparla y una serie de guardias que protegen al primero para darle tiempo y que complete el pase. Si existen flaquezas en esos aspectos, es posible que lanzar no sea la mejor de las opciones.

<img src="https://github.com/CharlyKill7/NFL-Success_Visualization/blob/main/images/pass_ratings.png" />

<details>
<summary>Average QB Rating by Team</summary>
<br>

 ![qb_rat](https://github.com/CharlyKill7/NFL-Success_Visualization/blob/main/images/qb_rat.png)
	
En este diagrama de barras vemos el "passer rating" medio por equipo, en función de si ganaron o no. Como ya aventuramos, parece que los mejores equipos de la liga están arriba en este gráfico, aunque hay excepciones que vale la pena mencionar. Baltimore Ravens, sexto equipo más exitoso del periodo estudiado, se encuentra entre los últimos en "passer rating". Pero, si echamos un vistazo a las tablas de la sección anterior, vemos que lo compensan con un número mayor de carreras, donde son más efectivos.

Otro caso interesante es el de Green Bay Packers, que supera con holgura a los mismísimos Patriots en este apartado. Esto se debe a la presencia de Aaron Rodgers, uno de los mejores QBs del siglo XXI. Como los Saints de Drew Brees, vuelcan su juega en el pase, y eso les hace ser más efectivos en general. 

</details>

<details>
<summary>Top Teams: Passer Rating</summary>
<br>

 ![top_rat](https://github.com/CharlyKill7/NFL-Success_Visualization/blob/main/images/top_rat.png)

</details>

<details>
<summary>Worst Teams: Passing Rating</summary>
<br>

![worst_rat](https://github.com/CharlyKill7/NFL-Success_Visualization/blob/main/images/worst_rat.png)

</details>
	
Como se puede apreciar en las dos tablas anteriores, los mejores equipos tienen, de media, un passer rating mayor. Sin embargo, hay equipos del Bottom 10 que superan en rating (Tennessee Titans 103.88) a equipos del Top 10 (Baltimore Ravens 96.69). Podríamos pues decir que aunque el passer rating influye, no es determinante en el éxito de un equipo o, dicho de otro modo, más vale correr si no tienes buen juego de pase. 

<br>

<a name="special"/>

## Special Teams
	
Si el Ataque y la Defensa son la cara y la cruz de la moneda NFL, el canto sería sin duda lo que se conoce como "Special Teams". Es el equipo de patada, donde el <em>kicker</em> o el <em>punter</em> patean para anotar o alejar el balón, respectivamente. Un lanzamiento a palos para conseguir tres puntos es un Field Goal, mientras que la patada que pretende alejar el balón se conoce como Punt. 

<img src="https://github.com/CharlyKill7/NFL-Success_Visualization/blob/main/images/spe_teams.png" />

<details>
<summary>Field Goald %</summary>
<br>

 ![fg](https://github.com/CharlyKill7/NFL-Success_Visualization/blob/main/images/fg.png)
	
Como vemos en el "Pie Chart", el porcentaje de acierto del Field Goal es mayor cuando se gana, aunque la diferencia no parece demasiado significativa. Esto se confirma con la gráfica inferior, donde podemos apreciar que las curvas son similares para diferencias de anotación muy amplias. Un mayor % de acierto es recomendable pero no decisivo para la victoria.

</details>

<details>
<summary>Punt Attempts</summary>
<br>

 ![punt](https://github.com/CharlyKill7/NFL-Success_Visualization/blob/main/images/punt.png)

Con los punt sucede más o menos lo mismo, puesto que el número de intentos es similar entre victorias y derrotas, y las gráficas son prácticamente paralelas para niveles de puntuación muy dispar. 

</details>

<details>
<summary>Field Goals by Team</summary>
<br>

![fg_teams](https://github.com/CharlyKill7/NFL-Success_Visualization/blob/main/images/fg_teams.png)

No obstante, en este último "Treemap" podemos observar (que no interactuar, para eso descargar y entrar en el archivo .pbix) que entre los equipos que más FGs anotan están la mayoría de conjuntos punteros de la liga, como los Patriots, los Seahawks o los Ravens. Es decir, tienen cierto peso específico en la victoria que sería un error desdeñar. 

</details>	

<br>
	
<a name="defense"/>

## Defense
	
En este apartado analizaremos, mediante la figura "Key Influencers" de PowerBI, las principales categorías estadísticas de la defensa para conocer su impacto en la victoria. Este es el aspecto genereal del gráfico:

<img src="https://github.com/CharlyKill7/NFL-Success_Visualization/blob/main/images/key1.png" />
	
Las principales estadísticas son:
- Interception: la defensa atrapa un pase lanzado por el quarterback rival y recupera la posesión. 
- Sack: la defenesa logra placar al quarterback rival antes de que lance el balon. 
- Safety: la defensa logra placar al ataque dentro de su propia zona de anotación, lo que se traduce en posesión y dos puntos extra. 
- Tackles: los placajes, el pan de cada día de la defensa. Cada vez que se tira al portador del balón al suelo se consigue un <em>tackle</em>.

<details>
<summary>Interceptions</summary>
<br>

 ![key1](https://github.com/CharlyKill7/NFL-Success_Visualization/blob/main/images/key1.png)

Cuando hay una intercepción (0.99 para ser exactos), la probabilidad de victoria se multiplica por 2,5 para el equipo que la consigue. A medida que aumenta el número, la victoria es cada vez más probable. 

</details>

<details>
<summary>Sacks</summary>
<br>

 ![key2](https://github.com/CharlyKill7/NFL-Success_Visualization/blob/main/images/key2.png)
	
Lo mismos sucede con los sacks, aunque no sean tan decisivos. Como vemos, la probabilidad de victoria es verdaderamente alta cuando la defensa consigue alcanzar al qb rival en cuatro o más ocasiones.  

</details>

<details>
<summary>Safeties</summary>
<br>

 ![key3](https://github.com/CharlyKill7/NFL-Success_Visualization/blob/main/images/key3.png)

En cuanto a los safeties, más de lo mismo. Conseguir al menos uno significa más opciones de llevarte la victoria. Es importante mencionar que lograrlo es algo relativamente raro y, por tanto, es un factor psicológico a considerar, pues que te hagan un "safety" suele desmoralizar al equipo.

</details>

<details>
<summary>Tackles</summary>
<br>

 ![key4](https://github.com/CharlyKill7/NFL-Success_Visualization/blob/main/images/key4.png)

Aquí, sin embargo, nos encontramos con la primera estadística defensiva que parece que, al aumentar, conlleva una menor probablidad de victoria. Esto es algo lógico, si entendemos que, cuanto más ataca el rival, más placajes tendrás que hacer. De hecho, el gráfico no deja dudas: cuantos menos placajes tengas que hacer por partido, más probable será ganarlo.

</details>

<br>		
<a name="conclusion"/>

## Conclusiones

Aunque podría haber concluido en la sección previa, voy a dibujar un balance de lo analizado:

- Generalmente, las jugadas de pase acercan más la victoria que las de carrera.
- Particularmente, lo anterior puede caer en excepción si tienes un passer rating bajo y un buen juego de carrera.
- Los equipos especiales, aunque merece la pena cuidarlos, no parecen tener tanto impacto directo en el resultado.
- La defensa y las grandes jugadas defensivas tienen una influencia decisiva en el resultado del partido. 
	
Como conclusión: 
<strong>La receta de la victoria tiene varios ingredientes, pero los principales son el juego de pase y, sobre todo, una gran defensa.</strong>
	
<br>
<br>
<br>
<br>
					<em>"Offense sells tickets, but Defense wins championships."</em> Bear Bryant.
	
<br>
<br>
