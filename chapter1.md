---
title: 'Objets de base'
description: "Ces exercices visent a vous familiariser avec le fonctionnement de R, les objets, l'environnement, etc.\n\nhttp://perso.ens-lyon.fr/lise.vaudor/Supports_formation/startR_1_objets_de_base.html"
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
- **Modifiez** la ligne de commande `c("World","le Monde")` pour **créer un objet** `obj_b`?

`@hint`
- Il s'agit simplement d'assigner le vecteur `c("World", "le Monde!")` à un objet `obj_b`!

`@pre_exercise_code`
```{r}
# Load datasets and packages here.
```

`@sample_code`
```{r}
ls()

obj_a <- c("Hello","Bonjour")
obj_b <- c("World","le Monde!")

ls()
```

`@solution`
```{r}
# Answer goes here
# Make sure to match the comments with your sample code
# to help students see the differences from solution
# to given.
```

`@sct`
```{r}
test_object("obj_a")
test_object("obj_b")
test_error()
success_msg("Vous savez maintenant créer des objets et modifier l'environnement (et faire un exercice sur Datacamp)!")
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
test_mc(correct = 2,
        feedback_msgs = c("Raté! Il y a deux petits pièges...",
                          "Oui, bravo! Avez-vous remarqué comme avec R il faut faire attention aux subtilités comme l'usage de guillemets?...",
                          "Eh non... vec3 contient des éléments de type caractère...",
                          "Non! 5 éléments entre 0 et 5, ça ne fait pas 0,1,2,3,4,5..."))
```

---

## Insert exercise title here

```yaml
type: NormalExercise
key: dac24444d5
xp: 100
```

Créez la tibble `starks` en précisant le **nom de famille de Jon** (à savoir "Snow") et en complétant le code de sorte que la table contienne **une variable "Age"** (numérique) correspondant aux âges des enfants Stark (respectivement 15, 14, 11, 9, 7 et 3 ans).

`@instructions`


`@hint`
Avez-vous bien précisé le nom de famille de Jon, et l'âge des enfants Stark en utilisant le bon type de variable (caractère pour les noms de famille, numérique pour l'âge)?

`@pre_exercise_code`
```{r}

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
ex()%>%test_object("starks")%>%check_equal()
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
test_mc(correct = 4,
        feedback_msgs = c("Non!",
                          "Non",
                          "Non",
                          "Oui, c'était bien Paris! Retenez bien l'usage des crochets [...] pour accéder à certains éléments de vecteurs.","Non"))
```
