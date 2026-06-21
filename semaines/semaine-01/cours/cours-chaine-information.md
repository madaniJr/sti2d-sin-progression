# La chaîne d'information — Cours

**Niveau :** Terminale STI2D — Spécialité SIN
**Séances concernées :** A et B — Semaine 1

---

## 1. Le système pluritechnique

Un système pluritechnique réalise une ou plusieurs **fonctions de service** en combinant des composants relevant de plusieurs domaines techniques (mécanique, électronique, informatique, optique…).

**Exemple :** une station météo connectée acquiert des grandeurs physiques (température, humidité, pression), les traite et les communique à distance.

Tout système pluritechnique peut être décomposé en deux chaînes complémentaires :

| Chaîne | Rôle |
|--------|------|
| **Chaîne d'information** | Acquérir, traiter et communiquer l'information |
| **Chaîne d'énergie** | Alimenter, distribuer, convertir et transmettre l'énergie |

---

## 2. La chaîne d'information

```
ACQUÉRIR ──► TRAITER ──► COMMUNIQUER
```

### 2.1 Acquérir

L'acquisition transforme une **grandeur physique** du monde réel en un signal exploitable par le système.

| Composant | Rôle | Exemple |
|-----------|------|---------|
| **Capteur** | Convertit la grandeur physique en signal électrique | Capteur de température (NTC, PT100), capteur de distance (ultrason, IR) |
| **Conditionneur** | Adapte le signal (amplification, filtrage, mise en forme) | Amplificateur opérationnel, pont de Wheatstone |
| **CAN** (Convertisseur Analogique-Numérique) | Convertit le signal analogique en valeur numérique exploitable par le processeur | CAN 10 bits de l'Arduino (0–1023) |

> **Remarque :** quand le capteur est déjà numérique (ex. DHT22, capteur I²C), l'étape CAN est intégrée au capteur.

### 2.2 Traiter

Le traitement analyse les données numérisées et produit une réponse adaptée.

| Composant | Rôle | Exemple |
|-----------|------|---------|
| **Microcontrôleur / microprocesseur** | Exécute le programme, applique les algorithmes de traitement | Arduino, Raspberry Pi, STM32 |
| **FPGA / DSP** | Traitement temps réel ou traitement du signal intensif | Traitement vidéo, asservissement rapide |

Le traitement peut inclure : calculs, comparaisons, prise de décision, stockage temporaire, communication avec d'autres modules.

### 2.3 Communiquer

La communication transmet l'information traitée vers l'extérieur (affichage, réseau, actionneur, utilisateur).

| Composant | Rôle | Exemple |
|-----------|------|---------|
| **CNA** (Convertisseur Numérique-Analogique) | Reconvertit une valeur numérique en signal analogique | Signal PWM pour commander un moteur |
| **Interface de communication** | Transmet l'information selon un protocole | UART, I²C, SPI, Wi-Fi, Bluetooth, LoRa |
| **Interface homme-machine (IHM)** | Présente l'information à l'utilisateur | Écran LCD, application web, voyant |

---

## 3. Schéma complet de la chaîne d'information

```
Grandeur      ┌─────────┐   Signal    ┌─────────────┐  Valeur  ┌──────────────┐
physique  ──► │ Capteur │ ──────────► │Conditionneur│ ───────► │     CAN      │
              └─────────┘  électrique └─────────────┘ analog.  └──────┬───────┘
                                                                       │ numérique
                                                                       ▼
                                                              ┌────────────────┐
                                                              │ Microcontrôleur│
                                                              │   (traitement) │
                                                              └───────┬────────┘
                                                                      │
                               ┌──────────────────────────────────────┤
                               │                                      │
                               ▼                                      ▼
                      ┌────────────┐                        ┌─────────────────┐
                      │    CNA     │                        │  Communication  │
                      └─────┬──────┘                        │ (réseau, IHM)  │
                            │                               └─────────────────┘
                            ▼
                      ┌──────────┐
                      │Actionneur│
                      └──────────┘
```

---

## 4. Notions de signal

### Signal analogique vs numérique

| Caractéristique | Signal analogique | Signal numérique |
|----------------|-------------------|-----------------|
| Valeurs possibles | Infinité (continu) | Discrètes (0 ou 1, ou ensemble fini) |
| Représentation | Courbe continue | Signal carré, train d'impulsions |
| Exemple | Tension de sortie d'un micro | Données sur bus I²C |

### Résolution du CAN

La résolution détermine la précision de la conversion :

```
Résolution = Vréférence / 2^n
```

- `n` = nombre de bits du CAN
- Arduino Uno : CAN 10 bits → 2¹⁰ = 1024 valeurs → résolution = 5V / 1024 ≈ **4,88 mV**

### Fréquence d'échantillonnage

Pour numériser un signal sans perte d'information, la fréquence d'échantillonnage `fe` doit respecter le **théorème de Shannon-Nyquist** :

```
fe ≥ 2 × fmax
```

où `fmax` est la fréquence maximale du signal à numériser.

---

## 5. Exemples de systèmes et leur chaîne d'information

### Station météo connectée

| Étape | Composant | Grandeur |
|-------|-----------|---------|
| Capteur | DHT22 | Température + humidité |
| Traitement | ESP32 | Calcul, mise en forme JSON |
| Communication | Wi-Fi (MQTT) | Données vers serveur |
| IHM | Application smartphone | Affichage |

### Système de régulation de température (chambre froide)

| Étape | Composant | Grandeur |
|-------|-----------|---------|
| Capteur | PT100 | Température |
| Conditionneur | Pont + ampli | Signal 0–5V |
| CAN | Microcontrôleur | Valeur numérique |
| Traitement | PID logiciel | Calcul de commande |
| CNA / actionneur | Relais + compresseur | Régulation |

---

## 6. Points clés à retenir

- La **chaîne d'information** traite le flux d'information : acquérir → traiter → communiquer.
- La **chaîne d'énergie** alimente le système et produit l'effet mécanique ou thermique.
- Un **capteur** convertit une grandeur physique en signal électrique.
- Le **CAN** numérise le signal analogique ; sa résolution dépend du nombre de bits.
- Le **microcontrôleur** est le cœur du traitement dans la plupart des systèmes embarqués.
- La **communication** peut être locale (bus série) ou distante (Wi-Fi, Bluetooth, LoRa).

---

## 7. Vocabulaire essentiel

| Terme | Définition |
|-------|-----------|
| Grandeur physique | Quantité mesurable du monde réel (température, pression, luminosité…) |
| Transducteur | Composant convertissant une énergie en une autre (dont les capteurs) |
| CAN | Convertisseur Analogique-Numérique |
| CNA | Convertisseur Numérique-Analogique |
| Protocole | Ensemble de règles définissant un échange de données |
| IHM | Interface Homme-Machine |
| Embarqué | Système informatique intégré dans un appareil dédié |

---

*Lycée Jean Rostand — STI2D SIN — Terminale*
