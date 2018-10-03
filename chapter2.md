---
title: 'Opérateurs et fonctions'
description: "Ces exercices visent a vous familiariser avec l'utilisation des operateurs et des fonctions.\n\nhttp://perso.ens-lyon.fr/lise.vaudor/Supports_formation/startR_2_operateurs_et_fonctions.html\n"
---

## Opérateurs arithmétiques

```yaml
type: NormalExercise
key: d5f0836347
xp: 100
```

Le script ci-contre crée deux vecteurs `pommes` et `bananes`. 

`@instructions`
**Complétez le script** pour créer un nouveau vecteur `fruits` qui correspond à la somme (élément par élément) des pommes et des bananes.

`@hint`
Ne réécrivez pas le vecteur `fruits` à la main! Il faut simplement ici réaliser une opération arithmétique simple à l'aide des vecteurs `pommes` et `bananes`...

`@pre_exercise_code`
```{r}
Ne réécrivez pas le vecteur `fruits` à la main! Il faut simplement ici réaliser une opération arithmétique simple sur les vecteurs `pommes` et `bananes`...
```

`@sample_code`
```{r}
bananes <- c(5, 2, 3, 1, 7 , 8,NA, 2)
pommes <-  c(2, 1, 0, 2, NA, 3, 1, 5)
```

`@solution`
```{r}
bananes <- c(5, 2, 3, 1, 7 , 8,NA, 2)
pommes <-  c(2, 1, 0, 2, NA, 3, 1, 5)
fruits <- pommes + bananes
```

`@sct`
```{r}
ex()%>%check_error()
ex()%>%check_object("fruits")%>%check_equal()
success_msg("Oui! Avez-vous remarqué comme NA+quelque chose donne NA?...")
```

---

## Opérateurs logiques

```yaml
type: PureMultipleChoiceExercise
key: c7aef84d29
xp: 50
```

Sachant que
`x<-33`

Laquelle de ces propositions renvoie FALSE?

`@hint`
(prop1 & prop2) est vraie si les deux propositions sont vraies
(prop1 | prop2) est vraie si au moins l'une des deux propositions est vraie...

`@possible_answers`
- x>10 | x>50
- x>=30 & x<=1000
- x>30 & x<10
- x %in% c(11,22,33,44,55)
- x<40

`@feedback`
ex()%>%check_mc(correct = 3,
                feedback_msgs = c("Non, cette proposition est vraie",
"Non, cette proposition est vraie",
"Eh oui! on ne peut pas avoir à la fois x>30 et x<10 donc quelle que soit la valeur de x, cette proposition est forcément fausse!",
"Non, cette proposition est vraie",
"Non, cette proposition est vraie"))

---

## Usage d'une fonction

```yaml
type: NormalExercise
key: d8589b3bba
xp: 100
```

L'environnement contient un vecteur `x`.

`@instructions`
Calculez la **moyenne**, la **variance**, et le **quantile d'ordre 90%** du vecteur x.

`@hint`
Avez-vous pensé à convertir la valeur 90% en une valeur comprise entre 0 et 1?

`@pre_exercise_code`
```{r}
set.seed(33)
x=rnorm(1000,3,2)
```

`@sample_code`
```{r}
moyenne <- ...
variance <- ...
quantile90p <- ...
```

`@solution`
```{r}
moyenne <- mean(x)
variance <- var(x)
quantile90p=quantile(x,0.9)
```

`@sct`
```{r}
ex()%>%check_error()
ex()%>%check_object("moyenne")%>%check_equal()
ex()%>%check_object("variance")%>%check_equal()
ex()%>%check_object("quantile90p")%>%check_equal()
```
