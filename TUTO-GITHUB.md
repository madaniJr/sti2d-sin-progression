# Tutoriel GitHub — Guide du professeur débutant

---

## C'est quoi Git et GitHub ?

**Git** = un outil installé sur votre ordinateur qui enregistre l'historique de vos fichiers.
**GitHub** = un site web qui héberge vos fichiers en ligne et permet de les partager.

Analogie simple :
> Git, c'est comme **Ctrl+Z illimité** pour tous vos fichiers, avec un journal de tout ce que vous avez fait.
> GitHub, c'est comme **une clé USB en ligne** accessible de partout.

---

## Les 5 concepts clés

| Terme | Définition simple |
|-------|-----------------|
| **Repository (repo)** | Votre dossier de projet en ligne |
| **Commit** | Une "sauvegarde" avec un message décrivant ce que vous avez changé |
| **Push** | Envoyer vos commits depuis votre PC vers GitHub |
| **Pull** | Récupérer les dernières modifications depuis GitHub vers votre PC |
| **Branch** | Une version parallèle du projet (ex. une version "brouillon") |

---

## Schéma du fonctionnement

```
Votre PC (VS Code)          GitHub (en ligne)
┌─────────────────┐         ┌──────────────────┐
│  Vos fichiers   │──push──►│  Votre dépôt     │
│  modifiés       │◄──pull──│  en ligne        │
│                 │         │                  │
│  git commit     │         │  Accessible par  │
│  (sauvegarde)   │         │  tout le monde   │
└─────────────────┘         └──────────────────┘
```

---

## Partie 1 — Créer un compte GitHub

1. Allez sur **https://github.com**
2. Cliquez sur **Sign up**
3. Renseignez : email, mot de passe, nom d'utilisateur
4. Vérifiez votre email

> Votre compte : **https://github.com/madaniJr** ✓ (déjà créé)

---

## Partie 2 — Installer les outils sur votre PC

### Git
1. Téléchargez sur **https://git-scm.com/download/win**
2. Installez avec les options par défaut
3. Vérifiez : ouvrez un terminal et tapez `git --version`

### GitHub CLI (gh)
1. Téléchargez sur **https://cli.github.com**
2. Installez, puis dans le terminal : `gh auth login`
3. Suivez les instructions (choisissez GitHub.com → HTTPS → browser)

### VS Code (éditeur)
1. Téléchargez sur **https://code.visualstudio.com**
2. Installez l'extension **"GitHub Pull Requests"** (optionnel mais utile)

---

## Partie 3 — Les commandes de base

Ouvrez un terminal (PowerShell ou le terminal intégré de VS Code).

### Naviguer dans les dossiers

```bash
# Voir où vous êtes
pwd

# Aller dans votre dossier de progression
cd "C:\Users\madan\Desktop\mehdi\sti2d-sin-progression"

# Lister les fichiers
ls
```

### Vérifier l'état de vos fichiers

```bash
git status
```

Ce que vous verrez :
- **rouge** = fichier modifié mais pas encore sauvegardé (pas encore "commité")
- **vert** = fichier prêt à être sauvegardé
- **rien** = tout est à jour

### Sauvegarder vos modifications (commit)

```bash
# Étape 1 : sélectionner les fichiers à sauvegarder
git add nom-du-fichier.md

# Sélectionner TOUS les fichiers modifiés
git add .

# Étape 2 : créer la sauvegarde avec un message
git commit -m "Ajout séance semaine 02"
```

### Envoyer sur GitHub (push)

```bash
git push
```

### Récupérer les modifications depuis GitHub (pull)

```bash
git pull
```

### Voir l'historique de vos sauvegardes

```bash
git log --oneline
```

---

## Partie 4 — Workflow type au quotidien

Voici ce que vous ferez à chaque fois que vous modifiez vos cours :

```
1. Ouvrez VS Code dans votre dossier
2. Modifiez / créez vos fichiers
3. Dans le terminal :
   git add .
   git commit -m "Description de ce que j'ai changé"
   git push
4. Vos fichiers sont en ligne sur GitHub ✓
```

### Exemple concret

Vous venez de créer la fiche pour la semaine 02 :

```bash
git add semaines/semaine-02/
git commit -m "Semaine 02 : protocoles de communication série"
git push
```

---

## Partie 5 — Travailler depuis un autre ordinateur

Si vous voulez travailler depuis le lycée ET chez vous :

### Premier téléchargement (une seule fois par ordinateur)

```bash
# Cloner = télécharger le projet depuis GitHub
git clone https://github.com/madaniJr/sti2d-sin-progression.git
```

Cela crée un dossier avec tous vos fichiers.

### Ensuite, avant chaque session de travail

```bash
# Toujours récupérer les dernières modifications avant de commencer
git pull
```

### Et après chaque session

```bash
git add .
git commit -m "Votre message"
git push
```

---

## Partie 6 — GitHub en ligne : l'interface web

Sur **https://github.com/madaniJr/sti2d-sin-progression** vous pouvez :

| Action | Comment |
|--------|---------|
| Voir vos fichiers | Cliquez sur un fichier, il s'affiche en rendu markdown |
| Modifier un fichier en ligne | Cliquez sur le fichier → icône ✏️ (crayon) |
| Voir l'historique | Onglet **Commits** |
| Partager avec les élèves | Copiez l'URL du fichier |
| Télécharger un fichier | Bouton **Raw** puis Ctrl+S |

---

## Partie 7 — Partager avec vos élèves

Votre dépôt est **public** : n'importe qui peut lire vos fichiers sans compte GitHub.

### Partager un fichier précis

Exemple : partager le TP B avec vos élèves

```
https://github.com/madaniJr/sti2d-sin-progression/blob/master/semaines/semaine-01/tp/tp-B-mesures-chaine.md
```

### Partager le dépôt entier

```
https://github.com/madaniJr/sti2d-sin-progression
```

Les élèves voient le `README.md` en page d'accueil avec la progression annuelle.

---

## Partie 8 — Les erreurs fréquentes et comment les régler

### "Nothing to commit"
> Vous n'avez modifié aucun fichier depuis le dernier commit. Normal.

### "Please tell me who you are" (premier commit)
```bash
git config --global user.name "Mohamed Madani"
git config --global user.email "mohamed.madani@lycee-jeanrostand.fr"
```

### "Rejected — fetch first"
> Quelqu'un (ou vous depuis un autre PC) a poussé des changements. Faites d'abord :
```bash
git pull
git push
```

### "Merge conflict"
> Deux versions du même fichier entrent en conflit. VS Code les affiche avec des marqueurs `<<<<` et `>>>>`. Choisissez quelle version garder, sauvegardez, puis :
```bash
git add .
git commit -m "Résolution du conflit"
git push
```

---

## Partie 9 — Aide-mémoire (à imprimer)

```
┌─────────────────────────────────────────────┐
│           COMMANDES GIT ESSENTIELLES        │
├─────────────────────────────────────────────┤
│ git status          → état des fichiers     │
│ git add .           → préparer tout         │
│ git commit -m "..." → sauvegarder           │
│ git push            → envoyer sur GitHub    │
│ git pull            → récupérer depuis GH   │
│ git log --oneline   → historique            │
└─────────────────────────────────────────────┘

WORKFLOW QUOTIDIEN :
  1. git pull   (si vous avez travaillé ailleurs)
  2. ... modifiez vos fichiers ...
  3. git add .
  4. git commit -m "ce que j'ai fait"
  5. git push
```

---

## Ressources pour aller plus loin

- **GitHub Docs en français** : https://docs.github.com/fr
- **Learn Git Branching** (interactif, visuel) : https://learngitbranching.js.org/?locale=fr_FR
- **Git - la référence** : https://git-scm.com/book/fr/v2

---

*Lycée Jean Rostand — Guide interne professeur*
