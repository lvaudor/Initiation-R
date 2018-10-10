---
title: 'GRAPHIQUES: BASES'
description: 'Ces exercices visent a vous familiariser avec le fonctionnement de base du package ggplot2'
---

## Jeu de données

```yaml
type: NormalExercise
key: 34ca4a8bb4
xp: 100
```

On considère le jeu de données diamonds, fourni par la librairie ggplot2.

`@instructions`
- **Examinez** le jeu de données `diamonds`
- **Complétez** le code ci-contre pour  tracer l'histogramme correspondant au prix des diamants (couleur de remplissage: `blue`).

`@hint`
Avez-vous bien spécifié le nom du tableau de données (`diamonds`, sans guillemets), le nom de la variable (`price`, sans guillemets) et la valeur du paramètre `fill` ("blue")?

`@pre_exercise_code`
```{r}

```

`@sample_code`
```{r}
library(ggplot2)
data(diamonds)
head(diamonds)

p <- ggplot(_____, aes(x=____)) +
  geom_histogram(fill=_____)

plot(p)
```

`@solution`
```{r}
library(ggplot2)
data(diamonds)
head(diamonds)

p <- ggplot(diamonds, aes(x=price)) +
  geom_histogram(fill="blue")
plot(p)
```

`@sct`
```{r}
ex()%>%check_error()
ex()%>%check_ggplot(exact_aes=TRUE, exact_geom=TRUE)
success_msg("Bien joué! vous avez fait votre premier graphique avec ggplot...")
```

---

## Choix de geom

```yaml
type: MultipleChoiceExercise
key: ece7f3d3a5
xp: 50
```

On considère le jeu de données `diamonds`. Ce jeu de données est fourni avec le package `ggplot2` et vous pouvez le charger dans la console ci-contre en chargeant le package puis le jeu de données

```{r}
library(ggplot2)
data(diamonds)
```

Pour en apprendre plus sur le contenu de ce jeu de données vous pouvez faire

```{r}
str(diamonds)
```


Examinez les données et répondez à la question suivante. Quel **geom** est le **plus approprié** si je souhaite tracer `price` (y) en fonction de `depth` (x)?

`@possible_answers`
- un geom de type **point**
- un geom de type **histogram**
- un geom de type **boxplot**

`@hint`
Les variables sont toutes deux numériques et continues...

`@pre_exercise_code`
```{r}

```

`@sct`
```{r}
ex()%>%check_mc(correct = 1,
        feedback_msgs = c("Oui, les deux variables sont numériques donc le nuage de point est tout indiqué...",
                          "Non, un histogramme serait approprié pour un graphique univarié!",
                          "Non, un boxplot serait approprié pour une variable x catégorielle..."))
```

---

## Geoms en tous genres

```yaml
type: NormalExercise
key: f5872fd309
xp: 100
```

`ggplot2` et `diamonds` ont déjà été chargés.

`@instructions`
**Complétez** le code pour créer:

- `p1`, un nuage de points montrant **price** (y) en fonction de **carat** (x)
- `p2`, un boxplot montrant **price** (y) en fonction de **cut** (x)
- `p3`, un barplot (`geom_bar`) montrant les effectifs de **cut** (x)

`@hint`
Il y a à chaque fois 3 éléments importants à spécifier: le **jeu de données**, les **variables x et** (éventuellement) **y**, et la **nature du geom**!

`@pre_exercise_code`
```{r}
require(ggplot2)
data(diamonds)
```

`@sample_code`
```{r}
# Graphique p1
p1 <- ggplot(diamonds, aes(x=___, y=___)) +
   ____()
plot(p1)

# Graphique p2
p2 <- ggplot(___________________________) +
  ______()
plot(p2)

# Graphique p3
p3 <- ______________________________________
  _____________
plot(p3)
```

`@solution`
```{r}
# Graphique p1
p1 <- ggplot(diamonds, aes(x=carat, y=price)) +
   geom_point()
plot(p1)

# Graphique p2
p2 <- ggplot(diamonds, aes(x=cut, y=price)) +
  geom_boxplot()
plot(p2)

# Graphique p3
p3 <- ggplot(diamonds, aes(x=cut)) +
  geom_bar()
plot(p3)
```

`@sct`
```{r}
ex()%>%check_error()
ex()%>%check_ggplot(index=1,exact_aes=TRUE, exact_geom=TRUE)
ex()%>%check_ggplot(index=2,exact_aes=TRUE, exact_geom=TRUE)
ex()%>%check_ggplot(index=3,exact_aes=TRUE, exact_geom=TRUE)
success_msg("Bien! Il y a encore bien d'autres geoms disponibles, mais `point` et `boxplot` sont des incontournables...")

```

---

## Paramétrer des geoms

```yaml
type: NormalExercise
key: 5405873c22
xp: 100
```

`ggplot2` et `diamonds` ont déjà été chargés.

`@instructions`
On a repris les 3 graphiques créés précédemment, mais cette fois on souhaite paramétrer les geoms. **Complétez le code** pour que

- dans `p1`, les **points** soient **bleus**
- dans `p2`, l'**intérieur des boîtes** soit **rouge**
- dans `p3`, les barres soient **transparentes (à 50%)**

`@hint`
Avez-vous bien trouvé le nom des paramètres qui vous intéressent?

- `color` pour la couleur de bordure, 
- `fill` pour la couleur de remplissage,
- `alpha` (valeurs entre 0 et 1) pour la transparence...

`@pre_exercise_code`
```{r}
require(ggplot2)
require(dplyr)
data(diamonds)
```

`@sample_code`
```{r}
p1 <- ggplot(diamonds, aes(x=carat, y=price)) +
   geom_point(___)
plot(p1)

# Graphique p2
p2 <- ggplot(diamonds, aes(x=cut, y=price)) +
  geom_boxplot(___)
plot(p2)

# Graphique p3
p3 <- ggplot(diamonds, aes(x=cut)) +
  geom_bar(____)
plot(p3)
```

`@solution`
```{r}
# Graphique p1
p1 <- ggplot(diamonds, aes(x=carat, y=price)) +
   geom_point(color="blue")
plot(p1)

# Graphique p2
p2 <- ggplot(diamonds, aes(x=cut, y=price)) +
  geom_boxplot(fill="red")
plot(p2)

# Graphique p3
p3 <- ggplot(diamonds, aes(x=cut)) +
  geom_bar(alpha=0.5)
plot(p3)
```

`@sct`
```{r}
ex()%>%check_error()

ex()%>%check_ggplot(index=1,exact_aes=TRUE, exact_geom=TRUE)
ex()%>%check_ggplot(index=2,exact_aes=TRUE, exact_geom=TRUE)
ex()%>%check_ggplot(index=3,exact_aes=TRUE, exact_geom=TRUE)

success_msg("Bien joué! Quelle joie, vous allez pouvoir customiser tous vos graphiques en rose!")
```

---

## Superposer des geoms

```yaml
type: NormalExercise
key: 6e4fcd9969
xp: 100
```

`ggplot2` et `diamonds` ont déjà été chargés.

`@instructions`
**Complétez le code** pour représenter la variable `table` du jeu de données `diamonds` en **superposant** deux geoms:

- un geom de type **histogram**, et de couleur de remplissage jaune
- un geom de type **rug**

`@hint`
Avez-vous bien fait appel 

- à la fonction `ggplot()` (pour créer le graphique), 
- à `geom_histogram()` pour tracer l'histogramme,
- à `geom_rug`  pour rajouter le "rug"?

`@pre_exercise_code`
```{r}
require(ggplot2)
require(dplyr)
data(diamonds)
```

`@sample_code`
```{r}
p<-_____________________+
  _______________+
  ___________
plot(p)
```

`@solution`
```{r}
p <- ggplot(diamonds, aes(x=table)) +
  geom_histogram(fill="yellow") +
  geom_rug()
plot(p)
```

`@sct`
```{r}
ex()%>%check_error()
ex()%>%check_ggplot(index=1,exact_aes=TRUE, exact_geom=TRUE)

success_msg("Bravo! Vous êtes en bonne voie pour faire des graphiques vraiment sympas!...")
```
