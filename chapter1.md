---
title: 'Objets de base'
description: "Ces exercices visent a vous familiariser avec le fonctionnement de R, les objets, l'environnement, etc.\n\nhttp://perso.ens-lyon.fr/lise.vaudor/Supports_formation/startR_1_objets_de_base.html"
---

## 1) Assignation

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

## Insert exercise title here

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
