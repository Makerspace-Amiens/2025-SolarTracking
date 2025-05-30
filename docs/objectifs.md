---
layout: default
nav_order: 3
title: Objectifs du projet
---

# Introduction

L’optimisation de la production d’énergie solaire représente un enjeu technique important dans le domaine des énergies renouvelables. Parmi les solutions explorées, l’amélioration de l’orientation des panneaux photovoltaïques permet d’augmenter leur rendement en captant davantage de rayonnement solaire au cours de la journée. Ce projet s’inscrit dans cette démarche d’optimisation, en proposant la conception d’un système capable d’ajuster automatiquement la position d’un panneau en fonction de la direction la plus lumineuse.

## Contexte du Projet

Dans un contexte de transition énergétique mondiale, les énergies renouvelables occupent une place centrale pour répondre aux enjeux environnementaux et réduire la dépendance aux énergies fossiles. Toutefois, leur adoption à grande échelle dépend aussi de leur performance et de leur rentabilité économique. Grâce à des avancées technologiques, notamment dans le domaine des capteurs, il devient aujourd’hui possible de rendre les installations photovoltaïques plus efficaces et attractives. Le projet s’inscrit donc dans cette dynamique, en exploitant les possibilités techniques actuelles pour valoriser l’énergie solaire.

## Objectifs du Projet

L’objectif principal du projet est de développer un suiveur solaire automatisé qui ajuste l’orientation d’un panneau photovoltaïque en fonction de la luminosité détectée sur plusieurs axes. En maximisant l’exposition du panneau au rayonnement solaire, ce système vise à améliorer son rendement énergétique et à rendre la production solaire plus compétitive, notamment en réduisant le coût du kilowatt-heure produit.

# Existant

## Ressources

-Logiciel CAO KidCad

-Visual Studio Code (C, C++)

-Arduino

-Découpeuse Laser

-Imprimante 3D


# Cahier des Charges

## Besoins fonctionnels

Le système doit pouvoir détecter la direction la plus lumineuse à l’aide de quatre photorésistances placées autour du panneau.

Le dispositif doit être capable de comparer en temps réel les valeurs des photorésistances afin de piloter les deux moteurs (axe horizontal et axe vertical).

Le panneau doit s’orienter automatiquement de manière fluide et précise.

## Composantes mécaniques
Base fixe

Sert de support stable au système complet.

Doit permettre un ancrage solide au sol ou sur un support plat.

Peut être réalisée en bois, métal ou plastique rigide.

Châssis rotatif horizontal

Permet la rotation du panneau sur un axe horizontal (gauche/droite).

Monté sur la base fixe à l’aide d’un servomoteur ou d’un moteur pas-à-pas.

Construit pour supporter la partie supérieure sans trop de jeu mécanique.

Support vertical inclinable (haut/bas)

Fixé sur le châssis horizontal.

Permet au panneau de s'incliner vers le haut ou le bas.

Cadre du panneau solaire

Supporte le panneau solaire.

Fixé au support vertical mobile.

Support des capteurs (LDR)

Bras ou boîtiers destinés à maintenir les 4 photorésistances aux coins du panneau.

Ces supports doivent limiter l’ombre projetée tout en assurant une bonne exposition à la lumière.

Compartiment électronique

Boîtier prévu pour protéger la carte Arduino, les connexions et l’alimentation.

Doit pouvoir se rendre accessible pour les tests et réglages.

## Modélisation & conception
Conception assistée par ordinateur (CAO) des pièces structurelles du suiveur solaire.

Réalisation de plusieurs versions de certaines pièces pour tester et améliorer l’assemblage.

Faire des vérifications d’encombrement et des ajustements pour assurer la compatibilité entre les pièces imprimées et les composants.

## Développement logiciel
Écriture d’un programme capable de lire les valeurs des quatre photorésistances.

Algorithme de comparaison pour déterminer la direction du soleil et ajuster l’orientation du panneau.

Pilotage des moteurs en fonction des résultats obtenus.

## Objectifs finaux
Avoir un prototype fonctionnel capable de suivre la lumière efficacement.

Améliorer le rendement de captation solaire par rapport à un panneau fixe.