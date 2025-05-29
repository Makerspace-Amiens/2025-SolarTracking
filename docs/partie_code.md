---
layout: default
nav_order: 10
title: Code
---

# Partie Code

`#include <Wire.h>
#include <BH1750.h>

BH1750 luxSensor;  

const int analogPin13 = 13;  
const int analogPin14 = 14; 
const int analogPin26 = 26; 
const int analogPin27 = 27; 

void setup() {
    Serial.begin(115200);  
    Wire.begin(21, 22);   // Initialisation de la communication I2C sur les pins 21 et 22 de l'ESP32
   
    delay(10000); // Délai pour permettre le démarrage du capteur BH1750

    // Initialisation du capteur BH1750 en mode haute résolution continue
    if (luxSensor.begin(BH1750::CONTINUOUS_HIGH_RES_MODE, 0x23)) {
        Serial.println("Capteur BH1750 initialisé !");
    }
}

void loop() {
    // Lecture de la luminosité (niveau de lumière)
    float lux = luxSensor.readLightLevel();  
   
    // Affichage de la luminosité sur le moniteur série
    /*Serial.print("Luminosité : ");
    Serial.print(lux);
    Serial.println(" lx");*/
   
    // Lecture de la valeur analogique sur GPIO15
    int adcValue13 = analogRead(analogPin13); // Lire la valeur ADC de GPIO15
    float voltage13 = adcValue13 * (3.3 / 4095.0); // Convertir la valeur ADC en tension (0-3.3V)
    int adcValue14 = analogRead(analogPin14); 
    float voltage14 = adcValue14 * (3.3 / 4095.0);
    int adcValue26 = analogRead(analogPin26); 
    float voltage26 = adcValue26 * (3.3 / 4095.0);
    int adcValue27 = analogRead(analogPin27); 
    float voltage27 = adcValue27 * (3.3 / 4095.0);

    /*Serial.print("Tension sur GPIO13 : ");
    Serial.print(voltage13);
    Serial.println(" V");
    Serial.print("Tension sur GPIO14 : ");
    Serial.print(voltage14);
    Serial.println(" V");
    Serial.print("Tension sur GPIO26 : ");
    Serial.print(voltage26);
    Serial.println(" V");
    Serial.print("Tension sur GPIO27 : ");
    Serial.print(voltage27);
    Serial.println(" V");*/

  Serial.print(lux, 3);   
  Serial.print(", ");   
  Serial.print(voltage13, 3);   
  Serial.print(", ");          
  Serial.print(voltage14, 3);   
  Serial.print(", ");
  Serial.print(voltage26, 3);   
  Serial.print(", ");
  Serial.print(voltage27, 3);   
  Serial.println();  

    // Attente d'une seconde avant la prochaine lecture
    delay(1000);  
}`

[](https://cloudlasalle.sharepoint.com/sites/TEAMS-AMS-PROJETI32-10SuiveurdePanneauSolaire/Documents%20partages/10%20Suiveur%20de%20Panneau%20Solaire/Programmation/Tracking/Tracking.ino?csf=1&web=1&e=h5DgaK)
