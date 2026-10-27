# S-PYTH-1023 — Comparer deux chaînes de caractères

## 1. Informations générales

| Élément | Description                                     |
|---|-------------------------------------------------|
| Référence | S-PYTH-1023                                     |
| Titre | Comparer deux chaînes de caractères             |
| Module | M-PYTH — Programmation Python                   |
| Thématique | Boucles, chaînes de caractères et algorithmique |
| Niveau | Débutant / intermédiaire                        |
| Environnement | Python 3.x                                      |
| IDE recommandé | PyCharm                                         |
| Projet support | Mini-projet Mastermind                          |

## 2. Thème de la séance

Comparer deux chaînes caractère par caractère afin d'identifier les caractères qui se trouvent à la même position.

Cette fonctionnalité constitue la première étape de programmation du projet Mastermind.

## 3. Situation professionnelle

Dans le mini-projet Mastermind, le joueur doit proposer une combinaison correspondant au code secret généré par le programme.

Le programme compare la proposition du joueur avec le code secret et détermine quels caractères sont correctement placés.

Exemple :

```python
code_secret = "RVBJ"
proposition = "RJBO"
```

Le programme doit comparer les deux chaînes position par position.

Résultat attendu :

```text
Bien placés : 2
```

Les caractères correctement placés sont :

- position 0 : `R` ;
- position 2 : `B`.

Les positions correspondantes sont donc `0` et `2`.

## 4. Objectif général

Être capable de comparer deux chaînes de caractères à l'aide de leurs positions, puis de transformer ce traitement en un module Python réutilisable.

## 5. Objectifs pédagogiques

À la fin de la séance, l'apprenant sera capable de :

- parcourir une chaîne de caractères avec une boucle `for` ;
- utiliser `range()` et `len()` ;
- accéder à un caractère avec son index ;
- comparer deux caractères avec l'opérateur `==` ;
- compter les caractères situés à la même position ;
- identifier les positions des caractères bien placés ;
- créer un module Python ;
- créer et appeler des fonctions ;
- utiliser correctement `return` ;
- retourner plusieurs informations depuis une fonction ;
- tester un module avec différentes propositions.

## 6. Prérequis

Avant de commencer, l'apprenant doit savoir utiliser :

- les variables et les chaînes de caractères ;
- l'indexation d'une chaîne ;
- les conditions `if` ;
- les opérateurs de comparaison ;
- les boucles `for` ;
- `print()`.

## 7. Accéder aux caractères d'une chaîne

Une chaîne de caractères peut être parcourue à l'aide de ses index. En Python, le premier caractère se trouve à l'index `0`.

Exemple :

```python
code_secret = "RVBJ"

print(code_secret[0])
print(code_secret[1])
print(code_secret[2])
print(code_secret[3])
```

Résultat :

```text
R
V
B
J
```

Chaque caractère possède une position, appelée **index**. Pour une chaîne de quatre caractères, les index sont `0`, `1`, `2` et `3`.

## 8. Comparer deux caractères

L'opérateur `==` permet de vérifier si deux valeurs sont égales.

```python
code_secret = "RVBJ"
proposition = "RJBO"

if code_secret[0] == proposition[0]:
    print("Même caractère")
```

À la position `0`, les deux caractères sont `R`. La condition est donc vraie et le message est affiché.

## 9. Comparer toutes les positions

Il faut maintenant comparer les caractères de toutes les positions des deux chaînes.

```python
code_secret = "RVBJ"
proposition = "RJBO"

for index in range(len(code_secret)):
    if code_secret[index] == proposition[index]:
        print("Bien placé")
```

Résultat :

```text
Bien placé
Bien placé
```

Deux caractères sont correctement placés.

### Comprendre le traitement

- `len(code_secret)` renvoie la longueur de la chaîne.
- `range(len(code_secret))` produit les index à parcourir.
- `index` prend successivement les valeurs `0`, `1`, `2` et `3`.
- `code_secret[index]` accède au caractère du code secret.
- `proposition[index]` accède au caractère de la proposition.
- `==` compare les deux caractères à la même position.

Dans cette première version, les deux chaînes sont supposées avoir la même longueur. Le contrôle de la saisie sera traité dans la séance S-PYTH-1026.

## 10. Compter les caractères bien placés

Pour connaître le nombre de caractères bien placés, il faut utiliser un compteur initialisé à zéro.

```python
code_secret = "RVBJ"
proposition = "RJBO"

bien_places = 0

for index in range(len(code_secret)):
    if code_secret[index] == proposition[index]:
        bien_places = bien_places + 1

print(f"Bien placés : {bien_places}")
```

Résultat :

```text
Bien placés : 2
```

À chaque fois que deux caractères sont identiques à la même position, le compteur est augmenté de `1`.

## 11. Identifier les positions des caractères bien placés

Le programme doit également pouvoir indiquer les positions des caractères bien placés.

Avec :

```python
code_secret = "RVBJ"
proposition = "RJBO"
```

Les caractères correctement placés sont :

```text
Position 0 : R
Position 2 : B
```

Les positions sont donc `0` et `2`.

### Travail demandé

Adapter le programme précédent pour conserver les positions des caractères bien placés. Pour cette première étape, le travail porte sur les chaînes de caractères et les boucles ; les listes ne doivent pas être utilisées.

Une possibilité consiste à construire une chaîne de caractères contenant les index trouvés, en ajoutant chaque position au fur et à mesure. Veiller à produire un affichage lisible.

## 12. Transformer le traitement en module Python

La fonctionnalité développée doit pouvoir être réutilisée par le programme principal du Mastermind.

Créer un fichier nommé :

```text
compar.py
```

Ce module devra contenir au minimum deux fonctions.

### Fonction 1 — Comparer les chaînes

Cette fonction devra :

- recevoir le code secret ;
- recevoir la proposition du joueur ;
- comparer les deux chaînes caractère par caractère ;
- compter les caractères bien placés ;
- identifier les positions des caractères bien placés ;
- retourner les résultats nécessaires au programme principal.

La fonction doit retourner suffisamment d'informations pour que le programme principal puisse afficher :

```text
Bien placés : 2
Positions : 0, 2
```

### Fonction 2 — Déterminer la victoire

La seconde fonction devra déterminer si le joueur a trouvé le code secret.

Elle devra vérifier si tous les caractères sont correctement placés et retourner une valeur booléenne :

- `True` si tous les caractères sont correctement placés ;
- `False` si au moins un caractère est mal placé.

### Choix des noms de fonctions

Les noms ne sont pas imposés. Ils doivent être :

- cohérents ;
- explicites ;
- représentatifs de la responsabilité de chaque fonction ;
- conformes à la convention Python `snake_case`.

Éviter les noms trop génériques, tels que :

```python
def fonction1():
    ...

def test():
    ...

def truc():
    ...
```

Le nom d'une fonction doit permettre de comprendre ce qu'elle fait. Vous pouvez réfléchir à des termes comme `comparer`, `bien_place`, `position`, `compter`, `victoire` ou `gagne`.

## 13. Comprendre `return`

L'instruction `return` permet à une fonction de transmettre un résultat au programme qui l'a appelée.

Dans cette séance, la fonction de comparaison doit transmettre :

- le nombre de caractères bien placés ;
- les positions de ces caractères.

La fonction qui détermine la victoire doit transmettre `True` ou `False`.

Le programme principal pourra ensuite afficher les résultats. Il est important de distinguer le fait d'afficher une valeur avec `print()` et celui de la retourner avec `return` : un affichage seul ne transmet pas automatiquement le résultat à l'appelant.

## 14. Exemple d'utilisation attendu

Le programme principal devra pouvoir importer les fonctions du module `compar.py`. Les noms ci-dessous sont illustratifs : remplacez-les par les noms réellement choisis dans votre module.

```python
from compar import nom_fonction_comparaison, nom_fonction_victoire

code_secret = "RVBJ"
proposition = "RJBO"

# Appeler ici la fonction de comparaison.
# Récupérer le nombre de caractères bien placés et leurs positions.

# Appeler ici la fonction qui détermine la victoire.
# Afficher les résultats obtenus.
```

Pour cet exemple, le résultat attendu est :

```text
Bien placés : 2
Positions : 0, 2
Gagné : False
```

Les noms `nom_fonction_comparaison` et `nom_fonction_victoire` sont des noms provisoires et ne doivent pas être utilisés tels quels dans le programme final.

## 15. Tests à réaliser

Tester le module avec plusieurs situations.

### Test 1 — Proposition incorrecte

Données :

```python
code_secret = "RVBJ"
proposition = "RJBO"
```

Résultat attendu :

```text
Bien placés : 2
Positions : 0, 2
Gagné : False
```

### Test 2 — Proposition correcte

Données :

```python
code_secret = "RVBJ"
proposition = "RVBJ"
```

Résultat attendu :

```text
Bien placés : 4
Positions : 0, 1, 2, 3
Gagné : True
```

### Test 3 — Aucun caractère bien placé

Choisir une proposition pour laquelle aucun caractère n'est identique au code secret à la même position.

Résultat attendu :

```text
Bien placés : 0
Positions : aucune
Gagné : False
```

### Test complémentaire

Créer au moins un test supplémentaire de votre choix et vérifier que le résultat correspond à ce qui est attendu.

> À cette étape, le traitement concerne uniquement les caractères **bien placés**. La recherche des caractères mal placés et la gestion des doublons seront abordées dans la séance S-PYTH-1024.

## 16. Travail demandé

1. Réaliser un premier programme qui compare les deux chaînes position par position.
2. Compter les caractères bien placés.
3. Identifier leurs positions sans utiliser de listes.
4. Créer le module `compar.py`.
5. Définir au minimum deux fonctions avec des noms explicites.
6. Utiliser `return` pour transmettre les résultats.
7. Tester les fonctions avec les trois situations proposées et un test supplémentaire.
8. Vérifier que le programme principal peut importer et utiliser les fonctions.

## 17. Production à remettre

À la fin de la séance, transmettre le fichier :

```text
compar.py
```

Le module devra :

- contenir au minimum deux fonctions ;
- utiliser des noms de fonctions explicites en `snake_case` ;
- comparer correctement les deux chaînes ;
- retourner le nombre de caractères bien placés ;
- retourner les positions des caractères bien placés ;
- retourner `True` ou `False` pour indiquer si le code est trouvé ;
- utiliser correctement `return` ;
- avoir été testé avec plusieurs propositions.

## 18. Critères de réussite

| Critère | Résultat attendu |
|---|---|
| Parcours des chaînes | Tous les index nécessaires sont parcourus |
| Comparaison | Les caractères sont comparés à la même position |
| Comptage | Le nombre de caractères bien placés est correct |
| Positions | Les index correspondants sont identifiés |
| Modularité | Le code est organisé dans `compar.py` |
| Fonctions | Au moins deux fonctions aux responsabilités claires |
| Valeurs retournées | Les résultats sont transmis avec `return` |
| Victoire | La fonction retourne `True` uniquement si le code est entièrement trouvé |
| Tests | Les situations proposées donnent les résultats attendus |

## 19. Pour préparer la séance suivante

La séance **S-PYTH-1024 — Rechercher les caractères mal placés** complétera la comparaison en identifiant les caractères présents dans le code secret mais positionnés ailleurs dans la proposition.

Cette prochaine étape introduira notamment l'opérateur `in`, la concaténation, `replace()` et la gestion des doublons.

---

**À retenir :** cette séance transforme un traitement simple — comparer deux caractères à la même position — en une fonctionnalité réutilisable. Elle permet de pratiquer les boucles et les chaînes de caractères tout en introduisant la conception de fonctions et le retour de résultats.
