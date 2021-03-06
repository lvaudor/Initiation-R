---
title: 'Objets de base'
description: "Ces exercices visent a vous familiariser avec le fonctionnement de R, les objets, l'environnement, etc.\n\n<a href=\"http://perso.ens-lyon.fr/lise.vaudor/Supports_formation/startR_1_objets_de_base.html\" target=\"_blank\"> Lien vers les diapos de cours </a>"
---

## Principe des exercices sur Datacamp

```yaml
type: NormalExercise
key: 4c8005af10
xp: 100
```

Cet exercice sert à vous montrer comment fonctionne la plateforme Datacamp...

`@instructions`
Ici, vous trouverez les consignes. Ici, imaginons que le but de l'exercice soit d'assigner la valeur 33 à l'objet a.

En face, vous avez:

- en haut un éditeur, et
- en bas une console R. L'environnement peut déjà contenir un certain nombre d'objets (des jeux de données par exemple).

Si vous ne parvenez pas à résoudre l'exercice, vous pouvez demander un indice, puis la solution (Take Hint puis Show Answer, ci-dessous)...

`@hint`
Avez-vous bien changé ___ en '33'?

`@pre_exercise_code`
```{r}

```

`@sample_code`
```{r}
# L'éditeur fonctionne (à peu de choses près) comme l'éditeur RStudio. Vous pouvez envoyer une ligne de code vers la console (en bas) en vous plaçant sur la ligne et en tapant Ctrl+Entrée sur votre clavier. Vous pouvez aussi envoyer l'ensemble de vos lignes de commandes en appuyant sur le bouton "Run code".

# Dans la plupart des exercices quelques lignes de commandes seront fournies, et ce sera à vous de les compléter en fonction des instructions.

a <- ___


# Les évaluations d'exercice consistent parfois à vérifier que la valeur de certains objets que vous avez créés correspond à ce qu'on attend...
# Essayez donc de ne pas changer leur nom au risque que la validation de votre exercice échoue...

# Si vous avez effacé certaines portions du code fourni au début et que vous estimez que c'était une erreur, vous pouvez appuyer sur le bouton "flèche en rond" (**reset sample code**).


#Une fois que vous avez complété et testé les lignes de commandes, et que vous pensez avoir la solution de l'exercice, vous pouvez **soumettre votre réponse** en appuyant sur le bouton "Submit". Un certain nombre de tests sont alors exécutés automatiquement pour déterminer si vous avez bien réussi l'exercice.

```

`@solution`
```{r}
a <- 33
```

`@sct`
```{r}
ex() %>% check_error()
ex() %>% check_object("a") %>% check_equal()
success_msg("Parfait! Vous allez pouvoir vous lancer dans les 'vrais' exercices...")
```

---

## Assignation

```yaml
type: NormalExercise
key: 94a29f0519
lang: r
xp: 100
skills: 1
```

La fonction **ls()** permet d'afficher l'**ensemble des objets disponibles dans l'environnement**.

`@instructions`
- Exécutez le code ci-contre et voyez comment l'environnement est modifié par l'exécution des deux commandes entre les appels à `ls()`.
- **Modifiez** la ligne de commande `c("pouet-pouet","tut-tut")` pour **créer un objet** `obj_b` correspondant à ce vecteur

`@hint`
- Il s'agit simplement d'**assigner** le vecteur à un objet `obj_b`!

`@pre_exercise_code`
```{r}
# Load datasets and packages here.
```

`@sample_code`
```{r}
ls()

obj_a <- c("coin-coin","ouaf-ouaf")
c("pouet-pouet","tut-tut")

ls()
```

`@solution`
```{r}
ls()

obj_a <- c("coin-coin","ouaf-ouaf")
obj_b <- c("pouet-pouet","tut-tut")

ls()
```

`@sct`
```{r}
ex()%>%check_error()
ex()%>%check_object("obj_a")%>%check_equal()
ex()%>%check_object("obj_b")%>%check_equal()
success_msg("Eh oui! Avant que vous fassiez la modification, le vecteur était créé à la volée, mais le résultat n'était pas 'stocké' dans l'environnement.")
```

---

## Création de vecteurs

```yaml
type: MultipleChoiceExercise
key: a6a92e2c32
xp: 50
```

Imaginons que je crée **quatre vecteurs** de la manière suivante:

- `vec1 <- 0:5`
- `vec2 <- seq(0,5,length.out=5)`
- `vec3 <- c("0","1","2","3","4","5")`
- `vec4 <- seq(0,5,by=1)`

Quels objets ont un contenu **identique**? (Ce code a été exécuté dans la console: vous pouvez examiner les objets en question...)

`@possible_answers`
- ils auront **tous un contenu identique**
- **vec1** et **vec4** ont un contenu identique
- **vec1**, **vec3** et **vec4** ont un contenu identique
- **vec1**, **vec2** et **vec4** ont un contenu identique

`@hint`
Examinez bien les objets... Leur longueur... la présence de guillemets...

`@pre_exercise_code`
```{r}
vec1 <- 0:5
vec2 <- seq(0,5,length.out=5)
vec3 <- c("0","1","2","3","4","5")
vec4 <- seq(0,5,by=1)
```

`@sct`
```{r}
ex()%>%check_mc(correct = 2,
                feedback_msgs = c("Raté! Il y a deux petits pièges...",
                                  "Oui, bravo! Avez-vous remarqué comme avec R il faut faire attention aux subtilités comme l'usage de guillemets?...",
                                  "Eh non... vec3 contient des éléments de type caractère...",
                                  "Non! 5 éléments entre 0 et 5, ça ne fait pas 0,1,2,3,4,5..."))				
```

---

## Création de tibble

```yaml
type: NormalExercise
key: dac24444d5
xp: 100
```



`@instructions`
Créez la tibble `starks` en précisant le **nom de famille de Jon** (à savoir "Snow") et en complétant le code de sorte que la table contienne **une variable "Age"** (numérique) correspondant aux âges des enfants Stark (respectivement 15, 14, 11, 9, 7 et 3 ans).

`@hint`
Avez-vous bien précisé le nom de famille de Jon, et l'âge des enfants Stark en utilisant le bon type de variable (caractère pour les noms de famille, numérique pour l'âge)?

`@pre_exercise_code`
```{r}
library(dplyr)
```

`@sample_code`
```{r}
starks <- tibble(FirstName=c("Robb","Jon","Sansa","Arya","Brandon","Rickon"),
                 LastName=c("Stark",...,"Stark","Stark","Stark","Stark"),
                 Age=...,
                 Direwolf=c("Grey Wind","Ghost","Lady","Nymeria","Summer","Shaggydog"))                                          
```

`@solution`
```{r}
starks <- tibble(FirstName=c("Robb","Jon","Sansa","Arya","Brandon","Rickon"),
                 LastName=c("Stark","Snow","Stark","Stark","Stark","Stark"),
                 Age=c(15,14,11,9,7,3),
                 Direwolf=c("Grey Wind","Ghost","Lady","Nymeria","Summer","Shaggydog"))
```

`@sct`
```{r}
ex()%>%check_error()
ex()%>%check_object("starks")%>%check_equal()
```

---

## Indexation des vecteurs

```yaml
type: MultipleChoiceExercise
key: 374baa2f54
xp: 50
```

L'environnement contient un objet `vecvilles`. Utilisez le **système d'indexation des vecteurs** pour répondre à la question suivante:

Quel est le **567ème élément** de `vecvilles`?

`@possible_answers`
- "Marseille"
- "Lyon"
- "Toulouse"
- "Paris"
- "Bordeaux"

`@hint`
Pour récupérer le i-ième élément d'un vecteur x: `x[i]`...

`@pre_exercise_code`
```{r}
set.seed(33)
vec <- c("Marseille","Lyon","Toulouse","Paris","Bordeaux")
vecvilles <- sample(vec,1000,replace=T)
```

`@sct`
```{r}
ex()%>%check_mc(correct = 4,
        feedback_msgs = c("Non!",
                          "Non!",
                          "Non!",
                          "Oui, c'était bien Paris! Retenez bien l'usage des crochets [...] pour accéder à certains éléments de vecteurs.",
                          "Non!"))
```

---

## Indexation d'une liste/d'une table

```yaml
type: NormalExercise
key: 27772afd1d
xp: 100
```

L'environnement contient deux objets: une liste `ma_liste` et une tibble `ma_tibble`.

`@instructions`
En **utilisant le système d'indexation** des objets de type liste et tibble,
- récupérez le 4ème élément de l'élément `fruits` dans l'objet `ma_liste` 
- récupérez les 6ème et 7ème éléments de la colonne `cri` dans l'objet ma_tibble

`@hint`
L'élément `fruits` est un vecteur => comment récupérer le quatrième élément d'un vecteur?
L'élément `cri` est un vecteur => comment récupérer les éléments 6 et 7 d'un _vecteur?_

`@pre_exercise_code`
```{r}
library(dplyr)
ma_liste=list(fruits=c("bananes","pommes","cerises","poires","abricots"),
              legumes=c("chou-fleur","poivron","carotte","poireau","brocoli","haricot","fenouil"),
              feculents=c("riz","pâtes","pommes de terre","semoule"))
ma_tibble=tibble(animal=c("chat","chien","âne","cheval","coq","cochon","vache"),
                 cri=c("miaou!","ouaf-ouaf!","hi-han!","hiihiiiihiiiii!","cocoricoo!","grouik!","meuh!"))
```

`@sample_code`
```{r}
quatrieme_fruit <- ...
quatrieme_fruit

sixieme_et_septieme_cris <- ....
sixieme_et_septieme_cris
```

`@solution`
```{r}
quatrieme_fruit <- ma_liste$fruits[4]
quatrieme_fruit

sixieme_et_septieme_cris <- ma_tibble$cri[6:7]
sixieme_et_septieme_cris
```

`@sct`
```{r}
ex()%>%check_error()
ex()%>%check_object("quatrieme_fruit")%>%check_equal()
ex()%>%check_object("sixieme_et_septieme_cris")%>%check_equal()
success_msg("Bravo! Retenez l'usage des crochets `[...]` pour indexer les objets!")
```
