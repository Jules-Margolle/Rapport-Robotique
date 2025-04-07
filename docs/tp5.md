---
layout: default
nav_order: 5
title: TP5 / FANUC ER-4ia
has_children: true
---

Ce TP a pour but grâce au bras robotisé de ranger et/ou placer les cubes imprimés en 3D. Des rails sont placés en face du robot, ces rails ont chacun une ouverture sur leur face supérieure afin d’y déposer les cubes et une ouverture en bas afin que l’on puisse les récupérer. De plus, entre les rails et le bras robotisé, se trouve une plateforme qui possède 9 encoches afin d’y placer minutieusement les cubes. Le but de ce TP est d’automatiser la prise puis le rangement des cubes et la prise puis la dépose des cubes. 

Pour ce robot, le principe reste le même que pour les autres robots et cobots étudiés précédemment. L’interface est identique, le fonctionnement et les settings aussi. 

Cela nous amène donc à la réelle difficulté de ce TP. Celui-ci nous demande en un minimum de lignes de programmation d’automatiser le processus de dépose/rangement. 

Pour ce faire, le robot doit effectuer que ce soit pour la prise ou la dépose les mêmes mouvements à ceci près qu’il doit se décaler d’un offset afin de déterminer le rail ou l’emplacement qu’il vise/utilise. Ainsi, nous avons décidé d’utiliser une boucle simple qui nous permet de répéter les mouvements. Tout comme dans les TP précédents, la position initiale du bras ou la position de replacement du bras au-dessus du plateau reste la même tout au long du code. Mais dans ce programme, nous devons adapter nos positions en fonction des rails et des emplacements, pour cela, nous avons utilisé l’outil « position register » qui nous permet de garder en mémoire à chaque itération de la boucle la position précédente ou n-1. Cela nous permet à la ligne suivante (et toujours dans notre boucle) d’ajouter un offset afin de décaler et de positionner parfaitement notre bras en fonction du décalage entre les rails ou entre les encoches. Une fois le processus réalisé et compris, il ne reste plus qu’à le répéter autant fois que nécessaire pour accomplir l’objectif du TP. 