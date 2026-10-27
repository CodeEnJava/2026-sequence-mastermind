# S-PYTH-1022 — Programmer un Mastermind en Python

## Présentation du projet

Ce dépôt accompagne la séquence pédagogique **S-PYTH-1022 — Programmer un Mastermind en Python**. Le Mastermind sert de fil conducteur pour apprendre à utiliser progressivement les boucles, les chaînes de caractères et les notions fondamentales d'algorithmique.

Le projet est construit étape par étape, depuis la comparaison de deux chaînes jusqu'à la réalisation d'un jeu complet jouable depuis la console.

> **Choix pédagogique :** les combinaisons sont représentées par des chaînes de caractères. Le parcours proposé évite volontairement les listes afin de consolider le travail sur les chaînes, les index et les boucles.

## Objectifs pédagogiques

À l'issue de la séquence, l'apprenant sera capable de :

- parcourir une chaîne de caractères avec une boucle `for` ;
- utiliser `range()` et `len()` ;
- accéder aux caractères à l'aide de leur index ;
- comparer deux chaînes caractère par caractère ;
- compter les caractères bien placés ;
- rechercher les caractères mal placés et prendre en compte les doublons ;
- reconstruire une chaîne ;
- utiliser une boucle `while` pour gérer les tours de jeu ;
- contrôler une saisie utilisateur ;
- utiliser `break` et `continue` ;
- générer aléatoirement un code secret ;
- assembler plusieurs traitements dans un programme complet.

## Prérequis

Il est recommandé de savoir utiliser :

- les variables et les chaînes de caractères ;
- `print()` et `input()` ;
- les conditions `if`, `elif` et `else` ;
- les opérateurs de comparaison ;
- les notions de base sur les boucles.

La séance **S-PYTH-1010 — Les tests conditionnels en Python** constitue un prérequis naturel.

## Environnement

- **Langage :** Python 3.x
- **IDE recommandé :** IDLE
- **Autre IDE possible :** PyCharm
- **Bibliothèque externe :** aucune
- **Module standard utilisé pour le code aléatoire :** `random`

## Progression des séances

| Référence | Séance | Notions principales |
|---|---|---|
| S-PYTH-1022 | Découverte du projet Mastermind | Présentation du jeu et de la progression |
| S-PYTH-1023 | Comparer deux chaînes | `for`, `range()`, `len()`, indexation, compteur |
| S-PYTH-1024 | Rechercher les caractères mal placés | `in`, concaténation, `replace()`, gestion des doublons |
| S-PYTH-1025 | Gérer les tours de jeu | `while`, compteur, condition d'arrêt, `break` |
| S-PYTH-1026 | Valider les saisies | `while`, `not`, `continue`, validation caractère par caractère |
| S-PYTH-1027 | Construire le Mastermind | `random.choice()` et assemblage des fonctionnalités |

Chaque séance ajoute une fonctionnalité qui sera réutilisée dans la suivante.

## Principe du jeu

Le programme doit progressivement permettre au joueur de :

1. recevoir un code secret ;
2. proposer une combinaison ;
3. comparer sa proposition au code secret ;
4. identifier les caractères bien placés ;
5. identifier les caractères présents mais mal placés ;
6. effectuer plusieurs tentatives ;
7. vérifier la validité des saisies ;
8. détecter la victoire ;
9. terminer la partie lorsque le nombre maximal d'essais est atteint.

Dans les exemples pédagogiques, les couleurs sont représentées par les lettres suivantes :

```python
COULEURS = "RVBJO"
```

Exemple de code secret et de proposition :

```python
code_secret = "RVBJ"
proposition = "RJBO"
```

La première étape consiste à compter les caractères qui se trouvent à la même position dans les deux chaînes. Les étapes suivantes permettront de prendre en compte les caractères mal placés, les doublons et les règles de saisie.

## Organisation recommandée du dépôt

```text
2026-sequence-mastermind/
├── README.md
├── cours/
│   ├── S-PYTH-1022-mastermind.md
│   ├── S-PYTH-1023-comparer-chaines.md
│   ├── S-PYTH-1024-caracteres-mal-places.md
│   ├── S-PYTH-1025-tours-jeu.md
│   ├── S-PYTH-1026-validation-saisies.md
│   └── S-PYTH-1027-mastermind.md
├── exemples/
│   ├── etape_01_votreprenom.py
│   ├── etape_02_votreprenom.py
│   ├── etape_03_votreprenom.py
│   ├── etape_04_votreprenom.py
│   └── mastermind_votreprenom.py
└── ressources/
    └── images/
```

Cette arborescence est une organisation recommandée. Les fichiers seront ajoutés au fur et à mesure de la progression pédagogique.

## Détail des étapes

### Étape 1 — Comparer deux chaînes

**Séance : S-PYTH-1023**

Comparer les caractères à chaque position et compter ceux qui sont identiques.

Exemple :

```text
Code secret : RVBJ
Proposition : RJBO
Bien placés : 2
```

Le travail porte notamment sur `for`, `range()`, `len()`, l'indexation et un compteur.

### Étape 2 — Rechercher les caractères mal placés

**Séance : S-PYTH-1024**

Après avoir identifié les caractères bien placés, rechercher les caractères présents dans le code secret mais positionnés ailleurs. La gestion des doublons doit être prise en compte.

Notions abordées : opérateur `in`, concaténation, immuabilité des chaînes et méthode `replace()`.

### Étape 3 — Gérer les tours de jeu

**Séance : S-PYTH-1025**

Permettre plusieurs propositions jusqu'à ce que le joueur trouve le code ou atteigne le nombre maximal de tentatives.

Notions abordées : `while`, compteur, condition d'arrêt, `break`, variable booléenne et condition de victoire.

### Étape 4 — Valider les saisies

**Séance : S-PYTH-1026**

Une proposition valide doit contenir exactement quatre caractères et utiliser uniquement les couleurs autorisées (`R`, `V`, `B`, `J`, `O`).

Notions abordées : `while`, `not`, `continue`, `for`, `in` et validation caractère par caractère.

### Étape 5 — Construire le jeu complet

**Séance : S-PYTH-1027**

Assembler les fonctionnalités précédentes et générer automatiquement un code secret à l'aide du module standard `random`.

Exemple de génération :

```python
import random

COULEURS = "RVBJO"
code_secret = ""

for _ in range(4):
    code_secret += random.choice(COULEURS)
```

Le jeu complet devra générer le code, demander et valider une proposition, calculer les résultats, gérer les tentatives, détecter la victoire et terminer la partie lorsque le nombre maximal d'essais est atteint.

## Méthode de travail

Pour chaque séance, suivre la démarche suivante :

1. **Comprendre** — lire les objectifs et les notions présentées.
2. **Observer** — étudier le programme proposé par le formateur.
3. **Expérimenter** — modifier le programme et observer les résultats.
4. **Pratiquer** — réaliser l'exercice demandé.
5. **Tester** — essayer plusieurs valeurs, y compris des cas limites.
6. **Corriger** — identifier et corriger les erreurs.
7. **Réinvestir** — réutiliser la notion dans le projet Mastermind.

Les consignes détaillées et les activités peuvent être diffusées sur LiliCampus. Le dépôt GitHub sert de référence pour le code source et les ressources associées.

## Défi final

À la fin de la séquence, réaliser une version fonctionnelle du Mastermind jouable depuis la console.

Des améliorations pourront ensuite être envisagées :

- modifier le nombre de tentatives ;
- modifier la longueur du code ;
- proposer plusieurs niveaux de difficulté ;
- améliorer l'affichage ;
- conserver l'historique des propositions ;
- ajouter un système de score.

## Critères de réussite

Le projet est considéré comme réussi lorsque l'apprenant sait :

- parcourir une chaîne de caractères ;
- utiliser `for`, `while`, `range()` et `len()` ;
- accéder aux caractères par index ;
- comparer deux chaînes ;
- rechercher et compter des caractères ;
- gérer les caractères en double ;
- valider une saisie utilisateur ;
- utiliser `break` et `continue` ;
- générer un code aléatoire ;
- assembler les traitements dans un programme complet.

## Licence et réutilisation

Les conditions de réutilisation du code et des ressources sont celles qui seront précisées dans le dépôt GitHub.

---

**À retenir :** le Mastermind est un support concret pour construire progressivement un programme plus complexe à partir de traitements simples, tout en réinvestissant les notions de chaînes de caractères, de boucles et d'algorithmique.
