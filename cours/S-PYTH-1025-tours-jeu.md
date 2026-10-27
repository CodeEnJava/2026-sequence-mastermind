# Séance S-PYTH-1025 — Gérer les tours de jeu

## Informations générales

- **Projet :** Mastermind en Python
- **Séance :** S-PYTH-1025
- **Thème :** gérer les tours de jeu
- **Pré-requis :** S-PYTH-1022, S-PYTH-1023 et S-PYTH-1024
- **Environnement :** Python 3.x, PyCharm ou un environnement de développement équivalent
- **Livrable :** un module Python permettant de gérer plusieurs propositions successives

---

## 1. Objectifs pédagogiques

À la fin de cette séance, vous devez être capable de :

- répéter une action tant qu'une condition est vraie avec une boucle `while` ;
- compter le nombre de propositions réalisées ;
- arrêter une boucle avec `break` lorsqu'une condition de victoire est satisfaite ;
- utiliser les résultats produits par les fonctions développées lors des séances précédentes ;
- distinguer la comparaison d'une proposition de la gestion globale d'une partie.

## 2. Contexte

Lors des séances précédentes, vous avez appris à comparer une proposition au code secret :

- compter les caractères bien placés ;
- compter les caractères présents dans le code secret mais mal placés ;
- déterminer si la proposition correspond exactement au code secret.

Jusqu'à présent, vous avez surtout testé ces opérations avec des valeurs définies directement dans le programme. Le but de cette séance est de répéter les propositions et de suivre le nombre de tours joués.

Pour cet exercice, on conserve les chaînes de caractères : le code secret et la proposition sont représentés par des chaînes de quatre caractères.

Exemple :

```python
code_secret = "RVBJ"
proposition = "RJBO"
```

Le code secret est ici fourni pour les tests. La génération aléatoire du code secret sera abordée lors de la séance S-PYTH-1027.

## 3. Notions à utiliser

### 3.1 La boucle `while`

Une boucle `while` répète un bloc d'instructions tant que sa condition est vraie.

```python
compteur = 0

while compteur < 3:
    print("Tour", compteur + 1)
    compteur = compteur + 1
```

Dans cet exemple, le compteur doit être modifié dans la boucle. Sinon, la condition pourrait rester vraie indéfiniment et provoquer une boucle infinie.

### 3.2 Le compteur de tours

Le compteur représente le nombre de propositions réalisées. Il doit être initialisé avant la boucle puis incrémenté à chaque tour.

```python
nombre_tours = 0
nombre_tours = nombre_tours + 1
```

L'incrémentation doit être placée à un endroit cohérent : une proposition effectivement traitée doit compter comme un tour.

### 3.3 L'instruction `break`

L'instruction `break` permet de sortir immédiatement de la boucle la plus proche.

```python
while True:
    # Traitement d'un tour
    if condition_de_victoire:
        break
```

Dans le projet, la condition de victoire doit être déterminée par la fonction développée à la séance précédente. Il ne faut pas confondre le nombre de caractères bien placés avec le résultat global de la comparaison : la victoire est obtenue lorsque le code proposé correspond exactement au code secret.

## 4. Travail demandé

### Étape 1 — Préparer le module

Dans le dépôt GitHub du projet, ouvrez le dossier prévu pour les séances Python et créez le fichier :

`jeu.py`

Si votre organisation de projet utilise un autre nom de module, conservez le nom demandé par votre formateur.

Le module doit réutiliser les fonctions de comparaison développées lors des séances S-PYTH-1023 et S-PYTH-1024. Adaptez les noms des fonctions importées aux noms réellement utilisés dans votre module `compar.py`.

### Étape 2 — Initialiser les variables

Préparez les variables nécessaires au suivi de la partie :

- `code_secret` : le code à découvrir ;
- `nombre_tours` : le nombre de propositions traitées ;
- `victoire` : indique si le code a été trouvé.

Pour commencer, utilisez un code secret fixe afin de tester le déroulement de la boucle.

### Étape 3 — Mettre en place la boucle de jeu

La boucle doit permettre de répéter les opérations suivantes :

1. afficher le numéro du tour ;
2. demander une proposition au joueur ;
3. incrémenter le compteur pour cette proposition ;
4. comparer la proposition au code secret en réutilisant les fonctions précédentes ;
5. afficher le nombre de caractères bien placés et mal placés ;
6. mettre à jour l'état de victoire ;
7. arrêter la boucle si le joueur a trouvé le code.

**Attention :** la validation des caractères autorisés et de la longueur de la proposition sera traitée à la séance S-PYTH-1026. Pour cette séance, concentrez-vous sur la boucle et le suivi des tours. Vous pouvez saisir une proposition de quatre caractères composée des caractères attendus.

### Étape 4 — Gérer la victoire

Lorsque la fonction de comparaison indique que la proposition correspond exactement au code secret :

- afficher un message de réussite ;
- afficher le nombre de tours réalisés ;
- quitter la boucle à l'aide de `break`.

Si la proposition est incorrecte, la partie doit continuer.

## 5. Consignes de réalisation

- Conservez les codes sous forme de chaînes de caractères.
- Réutilisez les fonctions des séances précédentes plutôt que de recopier leur logique.
- Utilisez un compteur clairement nommé, par exemple `nombre_tours`.
- Incrémentez le compteur une seule fois par proposition traitée.
- Utilisez `break` uniquement lorsque la condition de sortie prévue est satisfaite.
- Vérifiez que le programme ne s'arrête pas après une proposition incorrecte.
- N'ajoutez pas encore de génération aléatoire du code secret.
- Ne réalisez pas encore la validation complète des saisies : elle fera l'objet de la séance suivante.

## 6. Scénarios de test

Utilisez le code secret fixe suivant pour vos premiers tests :

```python
code_secret = "RVBJ"
```

| Test | Proposition(s) saisie(s) | Résultat attendu |
|---|---|---|
| 1 | `RVBJ` | La partie s'arrête après une proposition et annonce la victoire. |
| 2 | `RJBO`, puis `RVBJ` | La partie continue après la première proposition et s'arrête à la seconde. |
| 3 | Plusieurs propositions incorrectes, puis `RVBJ` | Le compteur correspond au nombre total de propositions traitées. |

Pour chaque test, vérifiez également que les nombres de caractères bien placés et mal placés correspondent aux résultats des fonctions de comparaison déjà testées.

## 7. Aide à la conception

Avant de coder, répondez aux questions suivantes :

1. Quelle valeur doit avoir `nombre_tours` au début de la partie ?
2. À quel endroit faut-il incrémenter le compteur ?
3. Quelle condition permet de savoir que le joueur a gagné ?
4. Pourquoi une proposition incorrecte ne doit-elle pas provoquer la sortie de la boucle ?
5. Quel est le rôle de `break` dans cette séance ?

Vous pouvez ensuite représenter le déroulement de la partie avec ce pseudo-code :

```text
Initialiser le code secret
Initialiser le compteur de tours
Initialiser l'état de victoire

TANT QUE la partie n'est pas gagnée
    Afficher le numéro du tour
    Demander une proposition
    Incrémenter le compteur
    Comparer la proposition au code secret
    Afficher les résultats
    SI le code est trouvé
        Afficher la réussite et le nombre de tours
        Sortir de la boucle
    FIN SI
FIN TANT QUE
```

## 8. Critères de réussite

Votre travail est terminé lorsque :

- [ ] la boucle `while` permet de jouer plusieurs tours ;
- [ ] le compteur est initialisé correctement ;
- [ ] le compteur augmente d'une unité pour chaque proposition traitée ;
- [ ] les résultats de comparaison sont affichés à chaque tour ;
- [ ] une proposition incorrecte permet de poursuivre la partie ;
- [ ] une proposition correcte provoque l'arrêt de la boucle avec `break` ;
- [ ] le nombre de tours est affiché en cas de victoire ;
- [ ] les fonctions développées lors des séances précédentes sont réutilisées.

## 9. Préparation de la séance suivante

La séance **S-PYTH-1026 — Valider les saisies** permettra d'améliorer la boucle en contrôlant les propositions avant de les traiter.

Vous apprendrez notamment à :

- répéter une demande tant que la saisie n'est pas valide ;
- utiliser `continue` pour ignorer une saisie incorrecte et revenir au début de la boucle ;
- vérifier la longueur de la proposition ;
- vérifier que les caractères saisis appartiennent aux caractères autorisés.

La génération aléatoire du code secret sera abordée ensuite, lors de la séance S-PYTH-1027.
