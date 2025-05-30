---
layout: default
nav_order: 4
title: Études et choix techniques
---

# Études et choix techniques

## Solution pour suivre le soleil

Dans le cadre d’un système de suivi solaire, il est essentiel de déterminer la position du soleil avec précision afin d’orienter correctement le panneau solaire. Pour ce faire, le choix d’utiliser quatre photorésistances (LDR) placées aux quatre coins du panneau s’impose comme une solution à la fois simple, économique et efficace.

Cette disposition permet de comparer l’intensité lumineuse reçue dans les quatre directions principales (haut, bas, gauche, droite). Lorsque le panneau n’est pas parfaitement orienté face au soleil, la lumière ne sera pas distribuée de manière uniforme sur les quatre photorésistances. Le système peut alors détecter quelle zone reçoit le plus de lumière et en déduire dans quelle direction ajuster l’orientation du panneau. Ce principe repose sur des écarts de luminosité relatifs, ce qui rend inutile toute calibration absolue de la lumière.

En plus d’offrir une bonne précision, cette méthode reste peu coûteuse et facilement implémentable sur une carte de développement comme une Arduino, avec un simple algorithme de comparaison. Enfin, elle fonctionne en temps réel et sans avoir recours à des calculs complexes d’angle solaire ou à des modules GPS, ce qui simplifie grandement le développement du système.

## Mécanique

Pour garantir un suivi solaire optimal, le système a été conçu autour d’une motorisation double, permettant une orientation biaxiale du panneau photovoltaïque. Ce choix repose sur le besoin d’ajuster la position du panneau selon deux axes : l’inclinaison verticale (élévation) et la rotation horizontale (azimut). Voici pourquoi nous avons retenu cette architecture.

Le premier moteur, directement fixé sur le support du panneau, est dédié à l’inclinaison verticale. Il permet de faire pivoter le panneau sur un angle d’environ 180 degrés, suivant la hauteur du soleil dans le ciel au cours de la journée. Cela permet de capter un maximum de lumière, notamment en matinée et en fin d'après-midi, lorsque le soleil est bas.

Le deuxième moteur, positionné un peu à l’écart du panneau, est relié à une courroie qui entraîne le support du panneau monté sur un roulement à billes. Ce système permet une rotation horizontale sur 360 degrés, offrant une grande liberté d’orientation autour de l’axe vertical. Ce mouvement est essentiel pour suivre le déplacement du soleil d’est en ouest tout au long de la journée.