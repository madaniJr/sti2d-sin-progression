# Exercice B — Application : chaîne d'information sur schémas variés

**Durée :** 20 min
**Niveau :** Terminale STI2D — SIN
**Modalité :** Individuel (papier)

---

## Exercice 1 — Thermostat connecté

Un thermostat connecté mesure la température ambiante et commande un radiateur électrique. Il envoie les données de température sur le réseau Wi-Fi et peut être piloté depuis une application smartphone.

**1a.** Complétez la chaîne d'information en plaçant les éléments suivants dans les bons blocs :
*Microcontrôleur ESP32 — Capteur NTC (thermistance) — Application smartphone — Module Wi-Fi — Amplificateur CAN interne — Relais de commande*

```
┌─────────────────┐   ┌─────────────────┐   ┌─────────────────┐   ┌─────────────────┐
│                 │──►│                 │──►│                 │──►│                 │
│   CAPTEUR       │   │ CONDITIONNEUR   │   │    TRAITEMENT   │   │  COMMUNICATION  │
│                 │   │    / CAN        │   │                 │   │                 │
└─────────────────┘   └─────────────────┘   └─────────────────┘   └─────────────────┘
```

**1b.** Le CAN de l'ESP32 est sur 12 bits et son alimentation est 3,3 V. Calculez sa résolution :

> Résolution = _______ V / 2^_______ = _______ mV

**1c.** La thermistance NTC a une résistance de 10 kΩ à 25°C. Sa tension de sortie est de 1,65 V à 25°C. Cette valeur est-elle dans la plage acceptée par le CAN de l'ESP32 ? Justifiez :

> _______________________________________________

---

## Exercice 2 — Système de contrôle d'accès par badge

Un système de contrôle d'accès lit un badge RFID, vérifie si l'accès est autorisé, et commande un verrou électromagnétique.

**2a.** Identifiez pour chaque composant son rôle dans la chaîne d'information :

| Composant | Rôle (acquérir / traiter / communiquer / actionner) |
|-----------|---------------------------------------------------|
| Lecteur RFID RC522 |  |
| Arduino Mega |  |
| Buzzer |  |
| Écran LCD I²C |  |
| Verrou électromagnétique |  |
| Module Ethernet W5500 |  |

**2b.** Le lecteur RFID communique avec l'Arduino via le protocole **SPI**. Cochez les caractéristiques de ce protocole :

- ☐ Communication série synchrone
- ☐ Communication parallèle
- ☐ Nécessite 4 fils (MOSI, MISO, SCK, SS)
- ☐ Nécessite 2 fils seulement
- ☐ Maître / Esclave
- ☐ Multi-maître natif

**2c.** Ce système dispose-t-il d'une chaîne d'énergie ? Si oui, identifiez-la brièvement :

> _______________________________________________

---

## Exercice 3 — Drone de livraison (analyse de cas)

Un drone de livraison embarque les capteurs suivants : GPS, baromètre, centrale inertielle (IMU), caméra, capteurs de distance ultrason. Il est contrôlé par un pilote automatique (Raspberry Pi 4 + carte Pixhawk).

**3a.** Pour chaque capteur, précisez la grandeur physique mesurée et le type de signal produit :

| Capteur | Grandeur physique mesurée | Signal produit (analogique / numérique / protocole) |
|---------|--------------------------|---------------------------------------------------|
| GPS |  |  |
| Baromètre |  |  |
| IMU (accéléromètre + gyroscope) |  |  |
| Caméra |  |  |
| Capteur ultrason |  |  |

**3b.** Le drone doit respecter le théorème de Shannon pour l'acquisition des données de l'IMU. Si la fréquence maximale des vibrations à détecter est de 200 Hz, quelle doit être la fréquence minimale d'échantillonnage ?

> fe ≥ _______ Hz

**3c.** Parmi les protocoles suivants, lesquels sont susceptibles d'être utilisés dans ce drone ? Justifiez votre choix :
*UART — I²C — SPI — CAN bus — Wi-Fi — 4G LTE — LoRa*

> _______________________________________________

---

## Corrigé (à destination du professeur)

<details>
<summary>Afficher le corrigé</summary>

### Exercice 1
**1a.** De gauche à droite : Capteur NTC → Amplificateur CAN interne → Microcontrôleur ESP32 → Module Wi-Fi → Application smartphone. Le relais est sur la chaîne d'énergie (commande de l'actionneur).

**1b.** Résolution = 3,3 V / 2¹² = 3,3 / 4096 ≈ **0,806 mV**

**1c.** Oui, 1,65 V est dans la plage 0–3,3 V acceptée par le CAN.

### Exercice 2
**2a.** Lecteur RFID : acquérir | Arduino : traiter | Buzzer : communiquer (signal sonore) | LCD : communiquer (IHM) | Verrou : actionner | Ethernet : communiquer (réseau)

**2b.** ✓ Communication série synchrone | ✓ Nécessite 4 fils | ✓ Maître / Esclave

**2c.** Oui : alimentation 12 V → verrou électromagnétique (énergie mécanique)

### Exercice 3
**3a.** GPS : position / NMEA (protocole série) | Baromètre : pression atmosphérique / I²C ou SPI | IMU : accélération + rotation / I²C ou SPI | Caméra : image / MIPI CSI ou USB | Ultrason : distance / signal PWM ou UART

**3b.** fe ≥ 2 × 200 = **400 Hz** minimum

**3c.** UART (GPS, liaison série) | I²C (baromètre, capteurs légers) | SPI (IMU haute fréquence) | CAN bus (communication robuste entre cartes) | 4G LTE (télécommande longue portée) | LoRa (transmission longue portée faible débit). Wi-Fi possible pour la télémétrie courte portée.

</details>

---

*Lycée Jean Rostand — STI2D SIN — Terminale*
