# S-PYTH-1022 — Découverte du projet Mastermind

## 1. Informations générales

| Élément | Description                                     |
|---|-------------------------------------------------|
| Référence | S-PYTH-1022                                     |
| Titre | Découverte du projet Mastermind                 |
| Module | M-PYTH — Programmation Python                   |
| Thématique | Boucles, chaînes de caractères et algorithmique |
| Niveau | Débutant / intermédiaire                        |
| Environnement | Python 3.x                                      |
| IDE recommandé | PyCharm                                         |
| Projet support | Jeu de Mastermind                               |

## 2. Présentation de la séance

Cette séance introduit un projet qui sera développé progressivement au cours de plusieurs séances de programmation Python : la réalisation d'un jeu de Mastermind jouable depuis la console.

Le Mastermind sert de fil conducteur pour réinvestir les connaissances déjà acquises et découvrir progressivement les boucles, le parcours des chaînes de caractères et les techniques de comparaison.

Le projet ne doit pas être réalisé intégralement dès cette première séance. L'objectif est d'en comprendre le fonctionnement, d'identifier les étapes de développement et de préparer le travail des séances suivantes.

## 3. Objectif général

Comprendre le fonctionnement du projet Mastermind et identifier les principales fonctionnalités qui seront programmées en Python au fil de la séquence.

À la fin de la séance, l'apprenant doit être capable d'expliquer :

- le principe général du jeu ;
- le rôle du code secret et de la proposition du joueur ;
- la différence entre un caractère bien placé et un caractère mal placé ;
- les grandes étapes de réalisation du programme ;
- les notions Python qui seront mobilisées.

## 4. Prérequis

Avant de commencer, l'apprenant doit connaître les notions suivantes :

- variables ;
- chaînes de caractères ;
- fonction `print()` ;
- fonction `input()` ;
- conditions `if`, `elif` et `else` ;
- opérateurs de comparaison ;
- premières notions sur les boucles.

La séance **S-PYTH-1010 — Les tests conditionnels en Python** constitue un prérequis naturel.

## 5. Principe du jeu

Le programme devra progressivement permettre à un joueur de retrouver une combinaison secrète.

Le jeu repose sur les éléments suivants :

1. un code secret généré par le programme ;
2. une proposition saisie par le joueur ;
3. une comparaison entre le code secret et la proposition ;
4. un résultat indiquant les caractères bien placés et mal placés ;
5. plusieurs tentatives possibles ;
6. une condition de victoire ;
7. une fin de partie lorsque le joueur a gagné ou atteint le nombre maximal de tentatives.

Le jeu sera réalisé dans un premier temps en mode console, sans interface graphique.

## 6. Représentation des combinaisons

Pour ce projet, les combinaisons seront représentées par des chaînes de caractères Python (`str`). Le parcours pédagogique évite volontairement les listes afin de travailler les chaînes, les index et les boucles.

Les couleurs sont représentées par les lettres suivantes :

```python
COULEURS = "RVBJO"
```

Chaque lettre correspond à une couleur disponible dans le jeu. Une combinaison comporte quatre caractères.

Exemple :

```python
code_secret = "RVBJ"
proposition = "RJBO"
```

Dans cet exemple, le programme devra comparer les caractères des deux chaînes en tenant compte de leur position.

## 7. Caractères bien placés et mal placés

### 7.1 Caractères bien placés

Un caractère est bien placé lorsque le caractère de la proposition est identique à celui du code secret à la même position.

Avec les valeurs suivantes :

```python
code_secret = "RVBJ"
proposition = "RJBO"
```

Les caractères `R` et `B` sont bien placés :

- position 0 : `R` ;
- position 2 : `B`.

Le résultat attendu pour cette étape est :

```text
Bien placés : 2
```

### 7.2 Caractères mal placés

Un caractère est mal placé lorsqu'il existe dans le code secret, mais qu'il n'est pas à la bonne position dans la proposition.

Cette fonctionnalité sera développée dans une séance ultérieure. Le traitement devra également tenir compte des caractères en double afin de ne pas compter plusieurs fois un même caractère du code secret.

## 8. Progression du projet

Le projet est divisé en cinq séances de développement, après cette séance d'introduction.

| Référence | Thème | Fonctionnalités et notions |
|---|---|---|
| S-PYTH-1023 | Comparer deux chaînes | Parcourir les caractères, utiliser `for`, `range()`, `len()`, l'indexation et un compteur |
| S-PYTH-1024 | Rechercher les caractères mal placés | Utiliser `in`, la concaténation, `replace()` et gérer les doublons |
| S-PYTH-1025 | Gérer les tours de jeu | Utiliser `while`, un compteur, une condition d'arrêt et `break` |
| S-PYTH-1026 | Valider les saisies | Contrôler la longueur et les caractères autorisés, utiliser `continue` |
| S-PYTH-1027 | Construire le Mastermind | Générer le code secret avec `random` et assembler les fonctionnalités |

Chaque séance ajoute une fonctionnalité au programme. Les traitements réalisés séparément seront réutilisés pour construire le jeu complet.

## 9. Les fonctionnalités attendues du programme final

À la fin de la séquence, le programme devra être capable de :

- générer un code secret composé de quatre caractères ;
- demander une proposition au joueur ;
- vérifier que la proposition contient exactement quatre caractères ;
- vérifier que seuls les caractères autorisés sont utilisés ;
- compter les caractères bien placés ;
- compter les caractères mal placés en tenant compte des doublons ;
- afficher les résultats de la comparaison ;
- gérer plusieurs tentatives ;
- détecter lorsque le code a été trouvé ;
- terminer la partie lorsque la victoire est obtenue ou que le nombre maximal d'essais est atteint.

## 10. Génération du code secret

La génération aléatoire sera abordée dans la dernière séance à l'aide du module standard `random`.

Le principe sera de choisir quatre fois un caractère parmi les couleurs autorisées et de construire progressivement une chaîne :

```python
import random

COULEURS = "RVBJO"
code_secret = ""

for _ in range(4):
    code_secret += random.choice(COULEURS)
```

Ce code est un aperçu de la fonctionnalité finale. Il ne constitue pas l'ensemble du jeu.

## 11. Méthode de travail

Pour chaque séance du projet, suivre cette démarche :

1. **Comprendre** : lire les objectifs et les notions présentées.
2. **Observer** : étudier l'exemple proposé par le formateur.
3. **Expérimenter** : modifier le code et observer les résultats.
4. **Pratiquer** : réaliser l'exercice demandé.
5. **Tester** : essayer plusieurs propositions, y compris des cas limites.
6. **Corriger** : repérer et corriger les erreurs.
7. **Réinvestir** : intégrer la fonctionnalité au projet Mastermind.

Il est recommandé de conserver une version fonctionnelle à chaque étape afin de pouvoir revenir à un traitement précédent si nécessaire.

## 12. Environnement de développement

Le projet peut être réalisé avec :

- Python 3.x ;
- IDLE, environnement recommandé pour la séquence ;
- PyCharm, si cet environnement est déjà utilisé.

Aucune bibliothèque externe n'est nécessaire. La génération aléatoire utilise le module `random`, fourni avec Python.

## 13. Organisation des ressources

Les ressources du projet peuvent comprendre :

- une fiche pédagogique pour chaque séance ;
- des vidéos explicatives ;
- des fichiers Python d'exemple ;
- des exercices ;
- des activités de test ;
- éventuellement des corrigés.

Les consignes détaillées et les activités peuvent être diffusées sur LiliCampus. Le dépôt GitHub sert de référence pour les fichiers de code et les ressources associées.

## 14. Travail demandé pendant cette séance

Après avoir pris connaissance du projet, l'apprenant doit être capable de présenter avec ses propres mots :

1. le but du jeu Mastermind ;
2. la signification du code secret et de la proposition ;
3. la différence entre caractères bien placés et mal placés ;
4. les principales étapes de réalisation du programme ;
5. les notions Python qui seront réutilisées.

Aucun jeu complet n'est attendu à cette étape. La programmation sera réalisée progressivement dans les séances suivantes.

## 15. Défi final

À la fin de la séquence, réaliser un Mastermind jouable depuis la console.

Une fois la version de base terminée, des améliorations pourront être envisagées :

- modifier le nombre maximal de tentatives ;
- modifier la longueur du code ;
- proposer plusieurs niveaux de difficulté ;
- améliorer l'affichage ;
- conserver l'historique des propositions ;
- ajouter un système de score.

## 16. À retenir

Le Mastermind est utilisé comme support pédagogique pour apprendre à construire un programme plus complexe à partir de traitements simples.

La progression suit cette logique :

```text
Chaînes de caractères
        ↓
Indexation
        ↓
Boucle for
        ↓
Comparaison
        ↓
Recherche des caractères
        ↓
Boucle while
        ↓
Validation des saisies
        ↓
Génération aléatoire
        ↓
Mastermind complet
```

L'objectif de la séquence est de réutiliser progressivement les notions Python dans un projet concret, plutôt que de les étudier indépendamment les unes des autres.
