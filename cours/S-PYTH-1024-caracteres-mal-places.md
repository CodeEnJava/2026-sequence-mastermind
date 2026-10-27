# S-PYTH-1024 — Rechercher les caractères mal placés

## 1. Informations générales

| Élément | Description                                     |
|---|-------------------------------------------------|
| Référence | S-PYTH-1024                                     |
| Titre | Rechercher les caractères mal placés            |
| Module | M-PYTH — Programmation Python                   |
| Thématique | Chaînes de caractères, boucles et algorithmique |
| Niveau | Débutant / intermédiaire                        |
| Environnement | Python 3.x                                      |
| IDE recommandé | PyCharm                                         |
| Projet support | Mini-projet Mastermind                          |

## 2. Thème de la séance

Compléter la comparaison du Mastermind en recherchant les caractères présents dans le code secret mais placés à une position différente dans la proposition du joueur.

Lors de la séance S-PYTH-1023, le programme a appris à compter les caractères **bien placés**. Dans cette séance, il faut déterminer les caractères **mal placés**, sans compter deux fois un même caractère du code secret.

## 3. Situation de départ

On dispose des deux chaînes suivantes :

```python
code_secret = "RVBJ"
proposition = "RJBO"
```

La comparaison position par position permet déjà d'identifier deux caractères bien placés :

- `R`, à la position `0` ;
- `B`, à la position `2`.

Il reste à rechercher les caractères qui sont présents dans le code secret et dans la proposition, mais qui ne sont pas à la même position.

Le résultat complet attendu pour cet exemple est :

```text
Bien placés : 2
Mal placés : 1
```

Le caractère `J` est présent dans le code secret et dans la proposition, mais à des positions différentes. Le caractère `O` n'est pas présent dans le code secret.

## 4. Objectif général

Être capable de rechercher les caractères mal placés dans deux chaînes de caractères, en tenant compte des caractères déjà identifiés comme bien placés et en évitant de compter plusieurs fois un même caractère du code secret.

## 5. Objectifs pédagogiques

À la fin de la séance, l'apprenant sera capable de :

- réutiliser la comparaison des caractères bien placés ;
- rechercher un caractère dans une chaîne avec l'opérateur `in` ;
- construire une nouvelle chaîne par concaténation ;
- expliquer que les chaînes de caractères sont immuables ;
- utiliser la méthode `replace()` ;
- distinguer les caractères bien placés des caractères mal placés ;
- prendre en compte les caractères en double ;
- intégrer le traitement au module Python développé lors de la séance précédente ;
- tester le résultat avec plusieurs propositions.

## 6. Prérequis

Avant de commencer, l'apprenant doit savoir utiliser :

- les variables et les chaînes de caractères ;
- l'indexation d'une chaîne ;
- les conditions `if` ;
- les boucles `for` ;
- `range()` et `len()` ;
- l'opérateur `==` ;
- la concaténation de chaînes ;
- les fonctions et l'instruction `return`.

Il est recommandé de reprendre le module réalisé lors de **S-PYTH-1023 — Comparer deux chaînes de caractères**.

## 7. Rappel : les caractères bien placés

Un caractère est bien placé lorsque les caractères du code secret et de la proposition sont identiques à la même position.

```python
code_secret = "RVBJ"
proposition = "RJBO"

bien_places = 0

for index in range(len(code_secret)):
    if code_secret[index] == proposition[index]:
        bien_places += 1

print(f"Bien placés : {bien_places}")
```

Résultat :

```text
Bien placés : 2
```

Pour compter correctement les caractères mal placés, il faudra éviter de recompter les caractères déjà reconnus comme bien placés.

## 8. Rechercher un caractère avec `in`

L'opérateur `in` permet de vérifier si un caractère se trouve dans une chaîne.

```python
code_secret = "RVBJ"
caractere = "J"

if caractere in code_secret:
    print("Le caractère est présent")
```

Résultat :

```text
Le caractère est présent
```

Si le caractère n'est pas présent, la condition est fausse.

### Travail d'expérimentation

Modifier les valeurs de `caractere` et tester les lettres `R`, `J` et `O`. Observer la différence entre un caractère présent et un caractère absent du code secret.

**Attention :** l'opérateur `in` indique seulement qu'un caractère existe dans la chaîne. Il ne suffit pas, à lui seul, à gérer correctement les doublons.

## 9. Construire une chaîne par concaténation

La concaténation consiste à assembler des chaînes avec l'opérateur `+`.

```python
caracteres = ""
caracteres = caracteres + "R"
caracteres = caracteres + "V"

print(caracteres)
```

Résultat :

```text
RV
```

Cette technique peut servir à construire progressivement une chaîne contenant uniquement les caractères qu'il reste à examiner.

L'apprenant doit veiller à initialiser la chaîne avant de lui ajouter des caractères.

## 10. Comprendre l'immuabilité des chaînes

En Python, une chaîne de caractères est **immuable** : ses caractères ne sont pas modifiés directement. Une opération qui produit une nouvelle chaîne renvoie un nouveau résultat.

Par exemple :

```python
code_secret = "RVBJ"
nouveau_code = code_secret.replace("R", "")

print(code_secret)
print(nouveau_code)
```

Résultat :

```text
RVBJ
VBJ
```

La variable `code_secret` conserve sa valeur initiale. Le résultat de `replace()` est affecté à `nouveau_code`.

Il est donc important de récupérer le résultat d'une opération de remplacement si l'on souhaite l'utiliser ensuite.

## 11. Utiliser `replace()` pour éviter les doublons

La méthode `replace(ancien, nouveau, nombre)` permet de remplacer des occurrences dans une chaîne. Le paramètre `nombre`, lorsqu'il est fourni, limite le nombre de remplacements.

Exemple :

```python
chaine = "RVRB"
nouvelle_chaine = chaine.replace("R", "", 1)

print(chaine)
print(nouvelle_chaine)
```

Résultat :

```text
RVRB
VRB
```

Dans cet exemple, une seule occurrence de `R` a été supprimée de la nouvelle chaîne.

Cette notion est utile pour éviter de compter plusieurs fois un même caractère lors de la comparaison des deux combinaisons.

## 12. Principe de recherche des caractères mal placés

Le traitement doit respecter les règles suivantes :

1. identifier les caractères bien placés ;
2. ne plus compter ces caractères dans la recherche des mal placés ;
3. rechercher les caractères de la proposition qui existent encore dans les caractères disponibles du code secret ;
4. lorsqu'un caractère est reconnu comme mal placé, le retirer des caractères disponibles afin qu'il ne soit pas compté une deuxième fois ;
5. compter les caractères mal placés.

Pour respecter ces règles, on peut construire des chaînes de travail qui représentent les caractères restant à examiner. Les chaînes originales doivent être conservées.

> La gestion des doublons est essentielle. Si le code secret contient un seul `R`, une proposition contenant plusieurs `R` ne doit pas permettre de compter plusieurs fois ce même `R`.

## 13. Exemple guidé

Données :

```python
code_secret = "RVBJ"
proposition = "RJBO"
```

### Étape 1 — Comparer les positions

| Position | Code secret | Proposition | Résultat |
|---:|---|---|---|
| 0 | R | R | Bien placé |
| 1 | V | J | Différent |
| 2 | B | B | Bien placé |
| 3 | J | O | Différent |

Il y a donc deux caractères bien placés : `R` et `B`.

### Étape 2 — Examiner les caractères restants

Après avoir écarté les caractères bien placés, il reste à examiner `V` et `J` dans le code secret, ainsi que `J` et `O` dans la proposition.

- `J` existe dans les caractères restants du code secret : il est mal placé.
- `O` n'existe pas dans les caractères restants du code secret : il n'est pas compté.

Résultat :

```text
Bien placés : 2
Mal placés : 1
```

## 14. Travail demandé : compléter le module

Reprendre le module Python créé lors de la séance S-PYTH-1023.

Ajouter une fonctionnalité permettant de déterminer le nombre de caractères mal placés.

Le module doit désormais permettre au programme principal d'obtenir :

- le nombre de caractères bien placés ;
- les positions des caractères bien placés ;
- le nombre de caractères mal placés ;
- l'information indiquant si le code a été trouvé.

Les noms des fonctions peuvent être choisis par l'apprenant, mais ils doivent rester explicites et respecter la convention `snake_case`.

Le code doit être organisé en fonctions réutilisables. Le programme principal se charge de récupérer les résultats et de les afficher.

## 15. Tests à réaliser

### Test 1 — Caractères bien et mal placés

Données :

```python
code_secret = "RVBJ"
proposition = "RJBO"
```

Résultat attendu :

```text
Bien placés : 2
Mal placés : 1
Gagné : False
```

### Test 2 — Tous les caractères bien placés

Données :

```python
code_secret = "RVBJ"
proposition = "RVBJ"
```

Résultat attendu :

```text
Bien placés : 4
Mal placés : 0
Gagné : True
```

### Test 3 — Aucun caractère présent à la bonne position ni ailleurs

Données :

```python
code_secret = "RVBJ"
proposition = "OOOO"
```

Résultat attendu :

```text
Bien placés : 0
Mal placés : 0
Gagné : False
```

### Test 4 — Vérifier la gestion des doublons

Données :

```python
code_secret = "RVBJ"
proposition = "RRRR"
```

Résultat attendu :

```text
Bien placés : 1
Mal placés : 0
Gagné : False
```

Le code secret ne contient qu'un seul `R`. Les autres occurrences de `R` dans la proposition ne doivent donc pas être comptées comme des caractères mal placés.

### Test complémentaire

Créer un autre test, notamment avec un caractère présent mais mal placé, et vérifier manuellement le résultat attendu.

## 16. Conseils de développement

- Conserver les valeurs originales de `code_secret` et `proposition`.
- Utiliser des chaînes de travail distinctes pour éliminer les caractères déjà traités.
- Ne pas confondre présence d'un caractère (`in`) et nombre d'occurrences.
- Lorsqu'un caractère est compté comme mal placé, le retirer des caractères disponibles pour éviter de le compter à nouveau.
- Vérifier les cas où aucun caractère n'est bien placé ou mal placé.
- Tester les doublons avant de considérer le traitement comme terminé.

## 17. Production à remettre

À la fin de la séance, transmettre le module Python mis à jour.

Le module devra :

- conserver le traitement des caractères bien placés ;
- calculer le nombre de caractères mal placés ;
- gérer correctement les doublons ;
- retourner les résultats au programme principal ;
- déterminer si le code est entièrement trouvé ;
- être organisé en fonctions aux responsabilités claires ;
- réussir les tests proposés.

## 18. Critères de réussite

| Critère | Résultat attendu |
|---|---|
| Caractères bien placés | Le comptage reste correct |
| Recherche | L'opérateur `in` est compris et utilisé à bon escient |
| Chaînes | La concaténation et l'immuabilité sont comprises |
| Remplacement | `replace()` est utilisé en tenant compte de sa valeur de retour |
| Caractères mal placés | Le comptage est correct |
| Doublons | Un caractère du code secret n'est compté qu'une seule fois |
| Modularité | Le traitement est organisé en fonctions |
| Tests | Les résultats correspondent aux cas attendus |

## 19. Préparer la séance suivante

La séance **S-PYTH-1025 — Gérer les tours de jeu** transformera les traitements de comparaison en une boucle de jeu permettant plusieurs propositions.

Les notions principales seront `while`, un compteur de tentatives, les conditions d'arrêt, `break` et la détection de la victoire.

---

**À retenir :** pour compter correctement les caractères mal placés, il ne suffit pas de rechercher si une lettre apparaît dans les deux chaînes. Il faut aussi tenir compte des caractères déjà bien placés et gérer les doublons afin qu'un même caractère du code secret ne soit pas compté plusieurs fois.
