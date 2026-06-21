# TP C — Modélisation SysML : BDD et IBD du système support

**Durée :** 60 min TP + 30 min mise en commun
**Niveau :** Terminale STI2D — SIN
**Modalité :** Individuel (ou binôme selon le logiciel disponible)

---

## Objectifs

- Construire le diagramme de définition de blocs (BDD) du système support
- Construire le diagramme de blocs internes (IBD) du système support
- Utiliser un logiciel de modélisation SysML (ou papier)

---

## Matériel et logiciels

- Système support (même que séances A et B)
- Dossier technique
- Résultats du TP B (schéma annoté, composants identifiés)
- Logiciel SysML : Modelio / Capella / draw.io / papier (selon disponibilité)

---

## Rappel méthodologique

Avant de commencer, relisez la méthode en 4 étapes du cours :
1. Identifier le système et ses frontières
2. Décomposer en blocs (→ BDD)
3. Connecter les blocs (→ IBD)
4. Vérifier la cohérence

---

## Partie 1 — Préparation (10 min)

**1.** Listez les blocs fonctionnels principaux que vous avez identifiés lors du TP B :

| Bloc | Rôle | Composant(s) physique(s) |
|------|------|--------------------------|
| 1 |  |  |
| 2 |  |  |
| 3 |  |  |
| 4 |  |  |

**2.** Listez les flux qui circulent entre ces blocs :

| Flux | De (bloc) | Vers (bloc) | Nature (données / énergie / signal) |
|------|-----------|-------------|-------------------------------------|
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |

---

## Partie 2 — Construction du BDD (25 min)

Construisez le BDD du système support. Votre BDD doit comporter :

- [ ] Le bloc racine (le système complet) avec le stéréotype `«block»`
- [ ] Au moins 3 sous-blocs de premier niveau (blocs fonctionnels)
- [ ] Des relations de composition (◆) ou d'association entre les blocs
- [ ] Les multiplicités sur les relations
- [ ] Pour chaque bloc : au moins un attribut (`values`) et un port si pertinent

### Critères de réussite

| Critère | Attendu |
|---------|---------|
| Bloc racine présent | Oui / Non |
| Relations de composition correctes | Oui / Partiellement / Non |
| Multiplicités renseignées | Oui / Non |
| Ports définis sur les blocs communicants | Oui / Non |
| Cohérence avec le système réel | Oui / Partiellement / Non |

---

## Partie 3 — Construction de l'IBD (25 min)

À partir de votre BDD, construisez l'IBD du système. Votre IBD doit comporter :

- [ ] Le titre : `ibd [block] NomDuSystème`
- [ ] Les instances des blocs définis dans le BDD (nom souligné)
- [ ] Les ports sur chaque instance
- [ ] Les connecteurs entre ports, étiquetés avec le nom du flux
- [ ] La direction des flux (flèches orientées)

### Questions d'analyse

**3.** Le flux de données est-il unidirectionnel ou bidirectionnel entre le capteur et le microcontrôleur ? Expliquez pourquoi :

> _______________________________________________

**4.** Existe-t-il un flux d'énergie dans votre IBD ? Si oui, lequel et comment l'avez-vous représenté ?

> _______________________________________________

**5.** Y a-t-il des blocs qui communiquent avec l'extérieur du système ? Lesquels et vers quel(s) acteur(s) ?

> _______________________________________________

---

## Partie 4 — Devoir maison

À rendre pour la séance suivante :

1. **Finaliser et soigner** le BDD et l'IBD (propre, légendé, lisible)
2. **Ajouter** pour chaque bloc du BDD :
   - Ses attributs (`values`) pertinents avec unités
   - Ses opérations principales
3. **Rédiger** un paragraphe de 5 à 8 lignes expliquant en langage naturel ce que représentent vos diagrammes et en quoi ils sont utiles pour comprendre le système

---

## Mise en commun — Correction collective (30 min)

Le professeur projette une solution de référence. Comparez avec votre travail :

| Point comparé | Ma version | Version de référence | Différence notée |
|---------------|-----------|---------------------|-----------------|
| Blocs de 1er niveau |  |  |  |
| Relations utilisées |  |  |  |
| Flux principaux |  |  |  |
| Erreurs identifiées |  |  |  |

**Ce que je dois corriger dans mon DM :**

> _______________________________________________

---

*Lycée Jean Rostand — STI2D SIN — Terminale*
