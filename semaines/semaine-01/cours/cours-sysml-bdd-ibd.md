# Modélisation SysML — BDD et IBD

**Niveau :** Terminale STI2D — Spécialité SIN
**Séance concernée :** C — Semaine 1

---

## 1. Pourquoi modéliser un système ?

La modélisation permet de :
- **représenter** un système complexe de façon structurée et lisible par tous les acteurs d'un projet
- **communiquer** entre ingénieurs, techniciens et clients sans ambiguïté
- **valider** une architecture avant de la réaliser (évite les erreurs coûteuses)

**SysML** (Systems Modeling Language) est le langage standard de modélisation des systèmes pluritechniques. Il est basé sur UML et adapté à l'ingénierie système.

---

## 2. Les diagrammes SysML au programme

SysML propose 9 types de diagrammes. En STI2D SIN, les principaux sont :

| Diagramme | Abréviation | Ce qu'il représente |
|-----------|-------------|---------------------|
| Block Definition Diagram | **BDD** | La structure statique : quels blocs composent le système |
| Internal Block Diagram | **IBD** | Les connexions internes entre blocs |
| Use Case Diagram | **UC** | Les interactions entre le système et ses acteurs |
| Sequence Diagram | **SD** | L'ordre chronologique des échanges |
| State Machine Diagram | **STM** | Les états et transitions d'un bloc |

Cette séance se concentre sur le **BDD** et l'**IBD**.

---

## 3. Le Block Definition Diagram (BDD)

### Principe

Le BDD décrit la **décomposition hiérarchique** du système : quels blocs le composent, et quelles relations (composition, association) les lient.

### Éléments graphiques

| Symbole | Signification |
|---------|--------------|
| Rectangle `«block»` | Un bloc (composant physique ou logiciel) |
| Losange plein ◆ | Composition (le bloc enfant appartient au bloc parent) |
| Losange vide ◇ | Agrégation (le bloc enfant peut exister indépendamment) |
| Flèche simple → | Association |
| Nombre (1, 0..*, 1..*) | Multiplicité |

### Structure d'un bloc

```
┌──────────────────────────┐
│        «block»           │
│     NomDuBloc            │
├──────────────────────────┤
│ values                   │  ← attributs mesurables (tension, température…)
│  + tension : V           │
├──────────────────────────┤
│ parts                    │  ← sous-composants
│  + capteur : Capteur     │
├──────────────────────────┤
│ ports                    │  ← points de connexion
│  + données : FluxDonnées │
├──────────────────────────┤
│ operations               │  ← comportements / fonctions
│  + acquérir()            │
└──────────────────────────┘
```

### Exemple — Station météo connectée (BDD)

```
                    ┌──────────────────────────┐
                    │        «block»           │
                    │   StationMétéo           │
                    └────────────┬─────────────┘
                                 │ composition ◆
          ┌──────────────────────┼────────────────────────┐
          │                      │                        │
┌─────────┴──────┐   ┌──────────┴──────┐   ┌────────────┴────────┐
│    «block»     │   │    «block»      │   │      «block»        │
│ ModuleAcquis.  │   │ Microcontrôleur │   │  ModuleCommunic.    │
└────────┬───────┘   └─────────────────┘   └─────────────────────┘
         │ ◆
    ┌────┴────┐
    │         │
┌───┴──┐ ┌───┴──┐
│«blk» │ │«blk» │
│DHT22 │ │BMP280│
└──────┘ └──────┘
```

---

## 4. L'Internal Block Diagram (IBD)

### Principe

L'IBD représente les **connexions internes** entre les blocs définis dans le BDD. Il montre les **flux** (données, énergie, matière) qui circulent entre les composants.

### Éléments graphiques

| Symbole | Signification |
|---------|--------------|
| Rectangle | Instance d'un bloc (avec son nom souligné) |
| Carré sur le bord □ | Port (point de connexion) |
| Flèche entre ports → | Connecteur (liaison entre deux ports) |
| Étiquette sur la flèche | Nature du flux (données, énergie, signal) |

### Types de ports

| Type | Notation | Rôle |
|------|----------|------|
| Port de flux | `«flowPort»` | Fait circuler un flux (donnée, énergie) |
| Port de service | `«port»` | Offre ou requiert un service |

### Exemple — Station météo connectée (IBD)

```
┌─────────────────────────────────────────────────────────────────────┐
│  ibd [block] StationMétéo                                           │
│                                                                     │
│  ┌─────────────┐   température   ┌──────────────┐   données JSON   │
│  │:ModuleAcquis│ ──────────────► │:Microcontrl. │ ───────────────► │►
│  └─────────────┘   humidité      └──────┬───────┘                  │
│                                         │ commande                 │
│                                         ▼                          │
│                                  ┌──────────────┐                  │
│                                  │:ModuleCommun.│                  │
│                                  └──────────────┘                  │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 5. Relation entre BDD et IBD

| BDD | IBD |
|-----|-----|
| Définit les blocs et leur hiérarchie | Montre comment les instances de ces blocs sont connectées |
| Vue **structurelle** (quoi ?) | Vue **comportementale** (comment ça circule ?) |
| Se construit en premier | Se construit à partir du BDD |

> **Règle :** on ne peut connecter dans un IBD que des blocs définis dans le BDD correspondant.

---

## 6. Méthodologie pour construire un BDD/IBD

### Étape 1 — Identifier le système et son contexte
- Quel est le système à modéliser ?
- Quelles sont ses frontières (ce qui est dedans / dehors) ?

### Étape 2 — Décomposer en sous-systèmes (BDD)
1. Créer le bloc racine (le système complet)
2. Identifier les grands blocs fonctionnels (acquisition, traitement, communication…)
3. Décomposer chaque bloc en composants physiques
4. Ajouter les attributs (`values`) et les ports si nécessaire

### Étape 3 — Connecter les blocs (IBD)
1. Instancier les blocs du BDD
2. Identifier les flux entre les blocs (données, énergie, signaux)
3. Relier les ports par des connecteurs étiquetés

### Étape 4 — Vérifier la cohérence
- Chaque port émetteur doit avoir un port récepteur compatible
- Les types de flux doivent être cohérents
- La décomposition BDD doit refléter la réalité physique du système

---

## 7. Erreurs fréquentes

| Erreur | Correction |
|--------|-----------|
| Confondre BDD et IBD | BDD = types de blocs ; IBD = instances connectées |
| Oublier les ports dans l'IBD | Chaque connexion passe obligatoirement par un port |
| Mettre des flèches dans le BDD sans étiquette | Préciser toujours le type de relation (composition, association) |
| Décomposer trop finement d'emblée | Commencer par les grands blocs, raffiner ensuite |
| Mélanger niveau physique et niveau logiciel | Distinguer les blocs matériels des blocs logiciels |

---

## 8. Logiciels de modélisation SysML

| Logiciel | Licence | Points forts |
|----------|---------|-------------|
| **Modelio** | Gratuit | Complet, conforme SysML, interface française |
| **Capella** | Gratuit | Conçu pour l'ingénierie système, puissant |
| **MagicDraw / Cameo** | Payant | Référence industrielle |
| **Papyrus** (Eclipse) | Gratuit | Intégré à Eclipse, configurable |
| **draw.io** | Gratuit en ligne | Rapide pour esquisses, pas de vérification SysML |

---

## 9. Points clés à retenir

- Le **BDD** définit les blocs et leur hiérarchie (vue statique).
- L'**IBD** montre les connexions et flux entre instances (vue des interactions internes).
- Les **ports** sont les points de connexion officiels entre blocs.
- On construit toujours le **BDD avant l'IBD**.
- SysML est un langage standardisé utilisé dans l'industrie (aéronautique, automobile, ferroviaire…).

---

*Lycée Jean Rostand — STI2D SIN — Terminale*
