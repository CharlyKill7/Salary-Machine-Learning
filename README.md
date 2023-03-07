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

En este proyecto habremos de visualizar los datos cargados tras efectuar una ETL, mediante el uso de herramientas como PowerBI, Tableau o ciertas librerías de Python como Matplotlib o Seaborn, con el fin mejorar el análisis de los mismos. En este caso concreto utilizaremos PowerBI, lo que podrá permitir, a cualquiera que no conozca los datos, entenderlos a golpe de vista.

### Restricciones:
- Utilizar una de las tres herramientas de visualización mencionadas.
- Practicar <em>storytelling</em>. 

### Dataset:
- <em>nfl_football_team_stats</em>: un archivo .csv con todas las estadísticas de juego de los equipos de la NFL entre 2010 y 2016.

### Objetivo:
 
Nuestro objetivo será presentar una serie de figuras gráficas que nos ayuden a dilucidar visualmente una cuestión planteada, que este caso será la siguiente:

<p><strong> ¿Qué factores del juego son más determinantes para el resultado final de un partido en la NFL?</strong>

 
 <a name="wins_by_team"/>
 
## Wins by Team

En primer lugar, parece lógico preguntarnos: ¿qué es el éxito en la NFL? La respuesta, para cualquier deporte, sería la misma: la victoria. Por ello, hemos decidido empezar adquiriendo una visión general de los equipos más existosos de la liga, para más adelante analizar las prácticas de cada conjunto en relación a su posición en esta primera gráfica.

<img src="https://github.com/CharlyKill7/NFL-Success_Visualization/blob/main/images/wins.png" />

Como podemos ver, para el periodo analizado hay un equipo sinónimo de éxito: New England Patriots. Es posible que, de analizar únicamente sus estadísticas, no podamos precisar qué aspecto del juego se debe priorizar, puesto que en la mayoría resultarían punteros. Por eso, vamos a dividir en tres los 32 equipos del gráfico. 

- Los Top Teams, los diez primeros, de New England Patriots a Kansas City Chiefs.
- Los Mid Teams, los doce intermedios, de Cincinnati Bengals a Los Angeles/San Diego Chargers.
- Los Worst Teams, los diez últimos, de Miami Dolphins a Cleveland Browns.

En este análisis vamos a utilizar el primer grupo y el último, buscando diferencias significativas en sus patrones de juego.

 <a name="pass_rush"/>
 
## Passing vs Rushing

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
