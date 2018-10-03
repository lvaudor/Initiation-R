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

---

## Arguments d'une fonction

```yaml
type: NormalExercise
key: 66ff3f31e9
xp: 100
```


La fonction **mean()** renvoie la moyenne d'un vecteur. 

L'existence d'un **élément manquant (NA)** dans le vecteur cause le renvoi de **NA** comme résultat. 

`@instructions`
Un des arguments de `mean()` permet de changer ce comportement pour renvoyer la moyenne du vecteur **en omettant les NA**. **Trouvez le nom de cet argument** en consultant l'aide de la fonction et **complétez** la deuxième commande (ci-contre) pour calculer `m2`.

Remarque: vous pouvez consulter le fichier d'aide associé à la fonction depuis l'interface Datacamp, comme vous le feriez depuis RStudio...

`@hint`
Avez-vous consulté l'**aide** de la fonction `mean()` (en tapant par exemple `help(mean)` ou `?mean`)  pour trouver le nom de l'argument qui nous intéresse ici?

`@pre_exercise_code`
```{r}

```

`@sample_code`
```{r}
vec <- c(3,2,8,NA,6,8,10,4,12,21,NA)

m1 <- mean(vec)
m2 <- mean(vec, _____)
```

`@solution`
```{r}
vec <- c(3,2,8,NA,6,8,10,4,12,21,NA)

m1 <- mean(vec)
m2 <- mean(vec, na.rm=T)
```

`@sct`
```{r}
ex()%>%check_error()
ex()%>%check_object("vec")
ex()%>%check_object("m1", incorrect_msg="Ne touchez pas à la commande qui crée m1")
ex()%>%check_object("m2")
success_msg("Très bien! Si l'on est assez facilement au clair sur ce que fait la fonction 'mean()', il y aura sans doute, à l'avenir, de nombreuses fonctions pour lesquelles vous aurez grand besoin de consulter l'aide!")
```

---

## Charger un package

```yaml
type: NormalExercise
key: 802104ce0c
xp: 100
```

L'environnement contient la tibble `starks`.

`@instructions`
On veut utiliser la fonction `filter` du package `dplyr`. Examinez l'erreur renvoyée par le code ci-contre et complétez-le pour que l'on parvienne à utiliser cette fonction et que le code ne génère plus d'erreur.

`@hint`
La fonction `filter()` n'est pas connue car le package n'a pas été chargé... En revanche, il est déjà installé!

`@pre_exercise_code`
```{r}
starks <- tibble(FirstName=c("Robb","Jon","Sansa","Arya","Brandon","Rickon"),
                 LastName=c("Stark","Snow","Stark","Stark","Stark","Stark"),
                 Age=c(15,14,11,9,7,3),
                 Direwolf=c("Grey Wind","Ghost","Lady","Nymeria","Summer","Shaggydog"))
```

`@sample_code`
```{r}
filter(starks, Lastname=="Stark")
```

`@solution`
```{r}
library(dplyr)
filter(starks, Lastname=="Stark")
```

`@sct`
```{r}
ex()%>%check_error()
```
