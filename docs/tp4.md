---
layout: default
nav_order: 4
title: TP4 / FANUC M710iC et M10iA
has_children: true
---

Ces robots conservent l’ancienne interface fanuc commune à la plupart des robots de la marque. Cela facilite ainsi la prise en main de ces deux robots. 

Le premier est un robot fanuc qui a pour but d’utiliser des pinces similaires à ceux utilisées sur des sites logistiques afin de supporter des palettes. Dans notre cas, nous utilisons notre robot pour qu’il porte et déplace plusieurs petites boîtes imprimées en 3D. 

Le second robot est quant à lui similaire au premier, toutefois ce bras robotisé possède un préhenseur équipé d’une pompe à vide avec lequel il a pour but de maintenir, dans le cas précis, une boîte en carton qui servira de réceptacle pour les boîtes en plastique. 

Ainsi l’utilisation de chacun des bras robotisés n’est pas forcément la tâche la plus complexe à réaliser si l’on considère les deux robots séparément. Pour autant, l’essence de ce TP réside dans le fait de synchroniser les mouvements et actions de ces robots afin que l’on parvienne à effectuer toutes les actions de manière ordonnées, précises et sans qu’il n’y ait aucun choc entre les 2 fanucs, cela tout en réalisant des mouvements d’une grande précision. 

Le TP demande en premier lieu que la boîte soit récupérée et que le carton soit positionné par le second robot sachant que la boîte et le carton arrivent sur des convoyeurs séparés. Les deux robots doivent donc communiquer afin de savoir s’ils sont “prêts” tous les deux, dans notre cas, il s’agit de savoir si le carton et la boîte sont saisis et correctement positionnés. 

Une fois le carton positionné, le premier robot doit placer et déposer la boîte à l’intérieur de celui puis se retirer. 

La dernière étape consiste quant à elle à déposer le carton sur un troisième convoyeur. 

Comme pour les TPs ou les robots précédents, on vient, après avoir défini les repères utilisateur et outils, créer et définir les trajectoires et les séquences de mouvements. Cela s’effectue avec l’utilisation de mouvement « joint » ou « linear » en fonction de la situation. Ces mouvements sont entrecoupés de différentes positions qui sont enregistrées dans le programme afin que les robots décrivent la trajectoire espérée. 

Enfin, l’adaptation a été de prendre en compte les mouvements des deux robots et des convoyeurs, pour cela, nous avons incorporé dans ce code des tempos avec conditions. Cela ordonne au premier robot d’attendre par exemple que le deuxième ait effectué une action définie, une fois celle-ci réalisée cela permet au premier robot de lire la suite de son programme et ainsi de suite pour les 2 bras. Avec cette méthode, nous avons réussi à synchroniser les mouvements des 2 robots. 

![Code fanuc pince](img/code_pince.jpg)

Si nous détaillons le code : 

Nous faisons aller les robots à une position initiale et on initialise les variables qui vont permettre de communiquer avec l’autre robot. Ici “fin depose” par exemple, est initialisée à “off” puisque c’est cette variable une fois sur “on” qui va indiquer que la boîte a été déposée. Ensuite nous attendons que la variable “autor prise” soit à “on” puisque cette variable indique que la boîte est arrivée à la fin du convoyeur et peut être récupérée. Le robot se déplace pour récupérer la boîte et se met en position pour mettre la boîte dans le carton. Pour cela, il faut que la variable “autor depose” passe à “on”. Cette variable est gérée par l’autre robot qui la passe à “on” lorsqu’il est en position pour accueillir la boîte. Une fois la boîte déposée, le robot passe la variable “fin depose” à “on” pour que l’autre robot puisse déposer le carton sur le dernier convoyeur. Enfin, le code se termine par un renvoie de label au début du code pour faire boucler le programme. 

Le principe de code est le même pour l’autre robot :

![Code fanuc pompe 1](img/code_ventouse_1.jpg)
![Code fanuc pompe 2](img/code_ventouse_2.jpg)


Ce TP nous a permis de découvrir la prise en main de deux robots plus imposants et les faire communiquer ensemble afin d'élargir nos possibilités quant au contrôle de robots industriels.

<video id="fanuc1" src="img/fanuc1.mp4" controls autoplay muted loop style="width: 100%;"></video>
<script>
  document.getElementById("fanuc1").muted = true;
</script>

<video id="fanuc2" src="img/fanuc2.mp4" controls autoplay muted loop style="width: 100%;"></video>
<script>
  document.getElementById("fanuc2").muted = true;
</script>