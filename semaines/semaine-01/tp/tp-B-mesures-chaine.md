# TP B — Identification et mesures sur la chaîne d'information

**Durée :** 90 min TP + 30 min compte-rendu
**Niveau :** Terminale STI2D — SIN
**Modalité :** Groupes de 2 à 3 élèves

---

## Objectifs

- Identifier et localiser chaque bloc fonctionnel de la chaîne d'information sur le système réel
- Réaliser des mesures électriques sur des points test définis
- Relier les mesures aux notions de signal analogique/numérique

---

## Matériel

- Système support (même que séance A)
- Dossier technique constructeur
- Multimètre numérique
- Oscilloscope (ou logiciel de visualisation)
- Fils de mesure, pinces crocodile

> **Rappel de sécurité :**
> - Ne jamais mesurer une tension > 50 V sans accord du professeur
> - Toujours brancher la masse (COM) en premier
> - Ne pas court-circuiter les bornes d'alimentation

---

## Partie 1 — Lecture du dossier technique (20 min)

À partir du dossier technique fourni, complétez le tableau :

| Bloc fonctionnel | Composant(s) du système | Référence constructeur | Grandeur traitée |
|-----------------|------------------------|----------------------|-----------------|
| Capteur |  |  |  |
| Conditionneur |  |  |  |
| CAN |  |  |  |
| Microcontrôleur |  |  |  |
| CNA / Interface de sortie |  |  |  |
| Communication |  |  |  |

**Question 1 :** Le capteur utilisé est-il analogique ou numérique ? Justifiez :

> _______________________________________________

**Question 2 :** Quelle est la tension d'alimentation du microcontrôleur ? Où la trouvez-vous dans le dossier ?

> _______________________________________________

---

## Partie 2 — Annotation du schéma (20 min)

Sur le schéma électronique fourni en annexe, annotez (en couleur ou avec des étiquettes) :

- En **rouge** : les blocs d'acquisition (capteur, conditionneur)
- En **bleu** : le bloc de traitement (microcontrôleur)
- En **vert** : les blocs de communication et IHM
- En **orange** : les alimentations

Repérez les **points test** indiqués sur le schéma (TP1, TP2…) et notez leur position dans le tableau :

| Point test | Localisation dans la chaîne | Signal attendu |
|------------|---------------------------|----------------|
| TP1 |  |  |
| TP2 |  |  |
| TP3 |  |  |

---

## Partie 3 — Mesures au multimètre (25 min)

Alimentez le système. Effectuez les mesures demandées avec le multimètre.

| Point de mesure | Grandeur mesurée | Valeur mesurée | Valeur attendue (dossier) | Écart |
|-----------------|-----------------|----------------|--------------------------|-------|
| Alimentation générale | Tension continue (V) | | | |
| Sortie capteur | Tension continue (V) | | | |
| TP1 | | | | |
| TP2 | | | | |

**Question 3 :** La valeur mesurée en sortie de capteur est-elle cohérente avec la grandeur physique mesurée ? (Comparez avec la caractéristique du capteur dans le dossier)

> _______________________________________________

---

## Partie 4 — Observation à l'oscilloscope (25 min)

Branchez l'oscilloscope sur les points test indiqués par le professeur.

**Mesure 1 — Signal en sortie du capteur (ou conditionneur)**

Réglez l'oscilloscope : Base de temps = ______ ms/div | Sensibilité = ______ V/div

Croquis du signal observé :

```
  V
  │
  │
  │
  │
  └────────────────────────────► t
```

- Nature du signal : ☐ Continu  ☐ Analogique variable  ☐ Numérique (logique)
- Tension min : _______ V | Tension max : _______ V | Période : _______ ms

**Mesure 2 — Signal sur le bus de communication (si accessible)**

- Type de signal observé : _______________________________________________
- Protocole identifié : ☐ UART  ☐ I²C  ☐ SPI  ☐ Autre : _______________

---

## Compte-rendu individuel (30 min)

Rédigez un compte-rendu comportant :

1. **Schéma annoté** de la chaîne d'information du système (blocs + noms des composants)
2. **Tableau de mesures** complété et commenté
3. **Réponse à la question de synthèse** :

> En vous appuyant sur vos mesures, expliquez le cheminement du signal depuis la grandeur physique mesurée par le capteur jusqu'à la sortie du système. Précisez les conversions effectuées (analogique → numérique, etc.).

---

## Grille d'évaluation formative (remplie par le professeur)

| Critère | Observé | Commentaire |
|---------|---------|-------------|
| Branchement correct du multimètre | ☐ Oui ☐ Partiellement ☐ Non | |
| Respect de la procédure de sécurité | ☐ Oui ☐ Partiellement ☐ Non | |
| Lecture correcte de la mesure | ☐ Oui ☐ Partiellement ☐ Non | |
| Branchement correct de l'oscilloscope | ☐ Oui ☐ Partiellement ☐ Non | |
| Réglage adapté de l'oscilloscope | ☐ Oui ☐ Partiellement ☐ Non | |
| Analyse du signal observé | ☐ Oui ☐ Partiellement ☐ Non | |

---

*Lycée Jean Rostand — STI2D SIN — Terminale*
