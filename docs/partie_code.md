---
layout: default
nav_order: 6
title: Code
---

# Partie Code

Dans le cadre de notre projet, nous avons développé et testé deux programmes visant à illustrer le fonctionnement d’un suiveur solaire. Cette section présente deux codes essentiels à la compréhension et à la démonstration de notre projet.

Premièrement, Le premier code est dédié à l’étude des photorésistances grâce l’utilisation du capteur de luminosité BH1750. Ce module permet de mesurer avec précision l’intensité lumineuse ambiante en lux et de mieux comprendre le comportement des capteurs face aux variations de lumière. Ces données sont fondamentales pour assurer une détection fiable de la source lumineuse.

Le second code correspond à la démonstration du suiveur solaire. Il met en œuvre les capteurs de luminosité pour piloter automatiquement l’orientation du panneau solaire en fonction de la position du soleil.

Ces deux codes sont complémentaires. Ils permettent de mieux appréhender les enjeux techniques de notre projet et démontrent son bon fonctionnement lors de la présentation finale.


## Test des photorésistances

Le premier code développé a pour objectif principal de calibrer les photorésistances utilisées dans notre système. Cette étape est importante afin de garantir une précision élevée lors de la détection de la luminosité ambiante.

Le code repose sur un affichage des valeurs en volts issues du pont diviseur constitué de la photorésistance et d’une résistance entre 100 Ω et 1000 Ω, permettant ainsi de mesurer la variation de tension en fonction de la lumière.

Dans ce code, nous avons comparé les valeurs obtenues par les photorésistances avec celles fournies par le capteur de luminosité BH1750. En observant les différences de valeurs entre les photorésistances, nous avons pu ajuster les paramètres du code afin d’obtenir une correspondance plus précise entre les photorésistances. Cependant l’ajustement a été abandonné par la suite car non nécessaire pour un prototype de tracking.

Il est important de noter que tous les tests ont été réalisés sur deux types de cartes différentes. Cependant, après analyse, nous avons décidé de retenir uniquement l’ESP32 S3 Xiao, qui a donné les meilleurs résultats en termes de stabilité et de performance pour ce projet.

```
#include <Wire.h>
#include <BH1750.h>

BH1750 luxSensor;

// Définition des constantes pour les pins analogiques
const int analogPinHG = A0;
const int analogPinHD = A1;
const int analogPinBG = A2;
const int analogPinBD = A4;

// Initialisation des tensions
float voltageadjHG;
float voltageadjHD;
float voltageadjBG;
float voltageadjBD;

void setup() {
  // Initialisation de la communication série
  Serial.begin(115200);

  // Initialisation de la communication I2C (SDA=4, SCL=5)
  Wire.begin(4, 5);
  delay(10000);

  // Initialisation du capteur BH1750
  if (luxSensor.begin(BH1750::CONTINUOUS_HIGH_RES_MODE, 0x23)) {
    Serial.println("Capteur BH1750 initialisé !");
  }
}

void loop() {
  // Lecture de la luminosité en lux
  float lux = luxSensor.readLightLevel();

  // Lecture des tensions sur chaque photorésistance
  int adcValueHG = analogRead(analogPinHG);
  float voltageHG = adcValueHG * (3.3 / 4095.0);

  int adcValueHD = analogRead(analogPinHD);
  float voltageHD = adcValueHD * (3.3 / 4095.0);

  int adcValueBG = analogRead(analogPinBG);
  float voltageBG = adcValueBG * (3.3 / 4095.0);

  int adcValueBD = analogRead(analogPinBD);
  float voltageBD = adcValueBD * (3.3 / 4095.0);

  // Affichage des valeurs sur le moniteur série
  Serial.print(lux, 3);
  Serial.print(", ");
  Serial.print(voltageHG, 3);
  Serial.print(", ");
  Serial.print(voltageHD, 3);
  Serial.print(", ");
  Serial.print(voltageBG, 3);
  Serial.print(", ");
  Serial.print(voltageBD, 3);
  Serial.println();

  // Pause d'une seconde entre deux mesures
  delay(1000);
}

```

## Programme de démonstration

Le projet repose sur l'utilisation de quatre photorésistances (HD, HG, BG, BD) disposées sur les coins du panneau solaire. Ces capteurs détectent la luminosité dans les différentes directions. Cela permet au système de déterminer où se trouve la source lumineuse la plus intense. Par la suite, en effectuant les lectures des capteurs, on ajuste automatiquement l'orientation du panneau en fonction de la variation de la lumière détectée.

## Explication du code

1- Lecture des valeurs des photorésistances : Les valeurs des quatre photorésistances sont lues à chaque cycle de la boucle principale. Ces valeurs sont converties en tensions analogiques (en volts), ce qui permet de comparer les intensités lumineuses sur les différentes zones du panneau.

2- Calcul des différences lumineuses : Ensuite, le code évalue les différences d'intensité lumineuse entre les différentes zones du panneau. Par exemple :

o Différence verticale entre les capteurs HG+HD (haut) et BG+BD (bas).

o Différence horizontale entre les capteurs HG+BG (gauche) et HD+BD (droite). Ces différences déterminent l'orientation du panneau, en ajustant ses servomoteurs pour que le panneau se tourne vers la zone la plus lumineuse.

3- Mouvement des servomoteurs :

o Mouvement horizontal : Si la différence lumineuse horizontale dépasse un certain seuil (toleranceH), le servomoteur horizontal ajuste la position du panneau pour se tourner vers la source de lumière.

o Mouvement vertical : Si la différence lumineuse verticale dépasse un seuil (toleranceV), le servomoteur vertical ajuste la position du panneau en hauteur pour s’orienter vers la lumière.

4- Retour à la position initiale : Si toutes les photorésistances ne détectent pas de lumière supérieure à un certain seuil (2.800 V), cela signifie que le panneau est dans une zone non lumineuse homogène ou que la lumière n’est pas assez diffuse.

## Détection de la lumière et ajustement dynamique

Ce mécanisme permet au panneau de suivre la position du soleil ainsi que d'autres sources lumineuses (directes ou réfléchies). Le système ajuste continuellement la position du panneau pour maximiser l'exposition à la lumière et garantir une captation d'énergie optimale.

Pour une utilisation en extérieur, il faut ajouter des caches pour réduire l'intensité lumineuse excessive. Cela évite que les capteurs réagissent à une lumière ambiante trop forte.

Pour finir, ce système ajuste dynamiquement l'orientation du panneau solaire en temps réel. Il se base sur les différences d'intensité lumineuse détectées par les photorésistances. Cela permet d'optimiser la captation d’énergie en orientant constamment le panneau vers la source lumineuse la plus intense.


```
#include <Wire.h>
#include <ESP32Servo.h>

// Initialisation des pins analogiques
const int analogPinHD = A0;
const int analogPinHG = A1;
const int analogPinBG = A2;
const int analogPinBD = A3;

// Déclaration des servomoteurs
Servo servoHorizontal;
Servo servoVertical;

// Position de base
int posH = 90;
int posV = 90;

// Pins des servomoteurs
const int pinServoH = D9;
const int pinServoV = D8;

// Tolérances de détection
const float toleranceV = 0.50;
const float toleranceH = 1.00;

// Angle vertical initial
int angle = 90;

void setup() {
  Serial.begin(115200);
  delay(1000);

  // Attachement des servos
  servoHorizontal.attach(pinServoH);
  servoVertical.attach(pinServoV);

  // Position initiale
  servoVertical.write(angle);
  servoHorizontal.write(95);
}

void loop() {
  // Lecture des tensions des photorésistances
  float hd = analogRead(analogPinHD) * (3.3 / 4095.0);
  float hg = analogRead(analogPinHG) * (3.3 / 4095.0);
  float bg = analogRead(analogPinBG) * (3.3 / 4095.0);
  float bd = analogRead(analogPinBD) * (3.3 / 4095.0);

  // Affichage des valeurs
  Serial.print(hd, 3); Serial.print(", ");
  Serial.print(hg, 3); Serial.print(", ");
  Serial.print(bg, 3); Serial.print(", ");
  Serial.print(bd, 3); Serial.println();

  // Calcul des différences de lumière
  float diff_verticale1 = (hg + hd) - (bg + bd);
  float diff_verticale2 = (bg + bd) - (hg + hd);
  float diff_horizontale1 = (hg + bg) - (hd + bd);
  float diff_horizontale2 = (hd + bd) - (hg + bg);

  // Mouvements horizontaux
  if (diff_horizontale1 > toleranceH) {
    servoHorizontal.write(90);   // Tourne dans un sens
    delay(160);
    servoHorizontal.write(95);   // Arrêt
  }
  else if (diff_horizontale2 > toleranceH) {
    servoHorizontal.write(97);   // Tourne dans l'autre sens
    delay(147);
    servoHorizontal.write(95);   // Arrêt
  }

  // Mouvements verticaux
  if (angle > 44 && angle < 136) {
    if (diff_verticale1 > toleranceV && angle < 126) {
      angle += 10;
      servoVertical.write(angle);
    }
    else if (diff_verticale2 > toleranceV && angle > 54) {
      angle -= 10;
      servoVertical.write(angle);
    }
  }

  // Repositionnement si lumière très forte partout
  if (hd > 2.800 && hg > 2.800 && bd > 2.800 && bg > 2.800) {
    servoVertical.write(90);
    angle = 90;
  }

  // Pause entre deux mesures
  delay(150);
}
 ```

## Optimisation du système de suivi solaire

Lors de l'utilisation du suiveur solaire en conditions réelles, il est important de prendre en compte la consommation énergétique du système. Elle peut être rapidement devenir trop élevée par rapport à la production d'énergie du panneau solaire. En effet, le fonctionnement continu des servomoteurs pour ajuster la position du panneau en temps réel entraîne une consommation importante de courant. Cela réduit l'efficacité globale du système.

## Augmenter le délai pour optimiser la consommation

Pour réduire la consommation, une première solution est d'augmenter les délais entre les ajustements de position. Chaque mouvement des servomoteurs consomme de l'énergie. Il est donc crucial de limiter les ajustements aux moments nécessaires. En augmentant le délai entre chaque cycle de mesure et de mouvement (par exemple, à 500 ms ou plus), le système effectuera des ajustements moins fréquents, réduisant ainsi la consommation d’énergie tout en maintenant un suivi lumineux efficace.

## Suivi théorique basé sur la trajectoire du soleil

Une autre approche pour optimiser le suivi solaire sans augmenter la consommation est le suivi théorique du soleil. En utilisant des données comme la latitude, la longitude et l'heure locale, on peut calculer la position du soleil et prédire l'orientation optimale du panneau à chaque instant. Cela réduit la fréquence des ajustements des servomoteurs et la charge énergétique.

Avec un modèle basé sur des calculs astronomiques (comme la position solaire), le système ajuste la position du panneau de manière plus précise et moins énergivore. Cette méthode théorique diminue la dépendance au suivi en temps réel tout en assurant une orientation optimale.

## Conclusion

En résumé, bien que le suivi solaire en temps réel offre des résultats précis, il consomme trop d'énergie par rapport à la production du système. Pour optimiser la consommation, il est conseillé d'augmenter les délais entre les ajustements et d'adopter un suivi théorique basé sur la trajectoire du soleil. Cette approche maximise l'efficacité tout en réduisant l'impact énergétique, offrant un bon compromis entre précision et performance.