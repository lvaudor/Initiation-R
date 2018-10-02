---
title: 'Objets de base'
description: "Ces exercices visent a vous familiariser avec le fonctionnement de R, les objets, l'environnement, etc.\n\nhttp://perso.ens-lyon.fr/lise.vaudor/Supports_formation/startR_1_objets_de_base.html"
---

## An exercise title written in sentence case

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
success_msg("Vous savez 
```
