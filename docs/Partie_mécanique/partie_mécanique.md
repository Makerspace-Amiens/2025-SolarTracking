---
layout: default
nav_order: 9
title: Partie Mécanique
has_children: true
---

# Partie Mécanique
---

## Pièces & Assemblage

Dans cette section, nous présentons les différentes pièces mécaniques et électroniques qui composent notre système, en détaillant leur rôle et leur fonctionnement dans l’ensemble du dispositif.

---

## Cache lumière

![](Images/support_ptd.png)

Le cache lumière est positionné aux quatre coins du panneau solaire. Il sert à empêcher que les faisceaux lumineux ne se croisent entre les différentes photorésistances. Cela permet à chaque capteur de mesurer une luminosité plus distincte, en fonction de l’orientation du soleil. Ainsi, le système peut plus facilement détecter les écarts et orienter le panneau avec plus de précision.

---

## Plateau du panneau solaire

![](Images/support_p.png)

Le plateau supporte le panneau solaire et permet son orientation face au soleil. Il s’agit de la partie mobile du système. Sa structure interne est conçue pour accueillir les composants électroniques : la carte PCB, la carte Arduino Xiao, ainsi que tout le câblage nécessaire. L’agencement de ce plateau facilite l’accès et l’entretien du circuit.

---

## Tenues de moteurs

![](Images/support_m.png)

Les supports moteurs permettent de fixer solidement les moteurs à leurs emplacements respectifs. Ils assurent la stabilité des moteurs pendant le fonctionnement et maintiennent l’alignement des axes de rotation.

---

## Rotation selon l’axe Y

![](Images/support_haut.png)

La rotation horizontale est assurée par un moteur pas à pas placé dans une pièce imprimée en rouge et fixé à la base verte. Ce moteur entraîne la structure supérieure par l’intermédiaire d’un palonnier métallique et d’une pièce en plastique. Cette configuration permet une orientation précise sur l’axe Est-Ouest, en fonction de la position du soleil.

---

## Rotation selon l’axe Z

![](Images/engrenages.png)

## Engrenage et transmission

La rotation verticale est assurée par un moteur à courant continu, couplé à un système d’engrenages. Grâce à une courroie GT2, l’effort du moteur est multiplié par un facteur 4, permettant de fournir le couple nécessaire à l’inclinaison du panneau.

Un roulement à billes 608ZZ est intégré au centre du support vert et de l’engrenage gris, assurant une rotation fluide autour de l’axe. L’ensemble est ensuite monté sur une tige filetée de 8 mm, bloquée entre deux écrous. Cela permet un axe libre et stable, que le moteur peut faire pivoter pour orienter le panneau en hauteur.

![](Images/supports_m.png)

---

## Tension de la courroie

![](Images/support_b.png)

Pour garantir une tension correcte de la courroie GT2, le moteur à courant continu est monté sur une plaque coulissante. Cette plaque est fixée à la base à l’aide de boulons,

insérés dans des rainures prévues à cet effet. Une tension optimale de la courroie est essentielle pour éviter les glissements ou imprécisions lors des mouvements du système.

---

## Intégration du système électronique et passage des câbles

Le circuit électronique est entièrement intégré à l’intérieur de la base rotative. Pour éviter que les câbles ne s’enroulent lors des rotations, ceux-ci passent à l’intérieur de la tige filetée, puis sont acheminés vers la base grâce à un slipring multibrin. Ce composant permet la transmission du courant entre les parties fixes et mobiles sans blocage ni torsion des fils.

---

## Assemblage final

![](Images/fini!.png)

L’assemblage final combine toutes les pièces mécaniques et électroniques dans un ensemble cohérent et fonctionnel. La structure permet un double axe de rotation, un câblage protégé et un accès simplifié aux composants internes.

<video width="600" controls>
  <source src="Images/video_meca.mov" type="video/mp4">
</video>