---
title: 'GRAPHIQUES: APPROFONDISSEMENT'
description: 'Ces exercices visent a vous apprendre à paramétrer de manière plus fine les axes et échelles associés à vos graphiques, et vous montrent comment ajouter des informations statistiques ou des modeles de regression à vos graphiques'
---

## Etiquettes et transformation d'axes

```yaml
type: NormalExercise
key: cd89155d0f
xp: 100
```

`ggplot2` et `diamonds` ont déjà été chargés.

`@instructions`
**Modifiez** le code ci-contre pour que: 

- les **étiquettes d'axes** soient "coupe" (en x) et "prix" (en y)
- l'**échelle des y** soient transformée par une **transformation log10**
- les **valeurs de l'axe x** soient traduites (en "Correcte","Bonne","Tres bonne","Premium","Ideale")

`@hint`
Avez-vous bien utilisé 

- la fonction `labs` pour les **étiquettes x et y**
- la fonction `scale_y_truc()` (remplacez `truc` par la formule appropriée) pour la **transformation de l'axe y**
- la fonction `scale_x_bidule()` (remplacez `bidule` par la formul appropriée) pour la **transformation de l'axe x**

**Consultez l'antisèche ggplot2!!!**

`@pre_exercise_code`
```{r}
require(ggplot2)
data(diamonds)
```

`@sample_code`
```{r}
p <- ggplot(diamonds, aes(x=cut, y=price)) +
  geom_boxplot(fill="pink") +
  _______ +
  _______ +
  _______
plot(p)
```

`@solution`
```{r}
p <- ggplot(diamonds, aes(x=cut, y=price)) +
  geom_boxplot(fill="pink") +
  labs(x="coupe",y="prix") +
  scale_y_log10() +
  scale_x_discrete(labels=c("Correcte","Bonne","Tres bonne","Premium","Ideale"))
plot(p)
```

`@sct`
```{r}
ex() %>% check_error()
fggplot <- ex() %>% check_function("ggplot")
fggplot %>% check_arg("mapping") %>% check_equal()
flabs <- ex() %>% check_function("labs")
flabs %>% check_arg("x")
flabs %>% check_arg("y")
ex() %>% check_function("scale_y_log10")
fscalex <- ex() %>% check_function("scale_x_discrete")
fscalex %>% check_arg("labels") 
success_msg("Oui! Vous savez maintenant customiser vos axes!!")
```

---

## Echelles de couleurs

```yaml
type: MultipleChoiceExercise
key: 237104581a
xp: 50
```

Imaginons que je souhaite produire un **nuage de points** montrant `carat` en fonction de `cut`, en faisant **varier la couleur en fonction de `price`**. 

**Quelle fonction** devrais-je utiliser pour éventuellement **modifier l'échelle colorée**? (consultez l'antisèche ggplot2!)

`@possible_answers`
- `scale_color_brewer()`
- `scale_fill_brewer()`
- `scale_color_gradient()`
- `scale_fill_gradient()`

`@hint`


`@pre_exercise_code`
```{r}

```

`@sct`
```{r}
ex()%>%check_mc(correct = 3,
        feedback_msgs = c("Non, `brewer` s'applique à des échelles **discrètes**, or `price` est **continu**",
                          "Non, car on s'intéresse à une couleur de **bordure** et non à une couleur de remplissage",
                          "Oui, bravo! **Retenez cette solution** pour l'exercice suivant...",
                          "Non, car on s'intéresse à une couleur de **bordure** et non à une couleur de remplissage"))
```

---

## Thème et échelle de couleur

```yaml
type: NormalExercise
key: 56d6e4a6c1
xp: 100
```

`ggplot2` et `diamonds` ont déjà été chargés, et un graphique produit.

`@instructions`
Modifiez le code qui vous est fourni ci-contre pour **reproduire cette figure**. 

Il s'agit de 

- **modifier le thème** 
- **modifier l'échelle colorée** pour que les prix **les plus bas** correspondent à la couleur **jaune** et les prix **les plus hauts** à la couleur **bleue**.

`@hint`
Avez-vous bien spécifié le bon thème (`theme_minimal()`) et utilisé la fonction `scale_color_gradient()`?

`@pre_exercise_code`
```{r}
library(ggplot2)
data(diamonds)
p <-ggplot(diamonds, aes(x=cut, y=carat,color=price))+
  geom_jitter() +
  theme_minimal()+
  scale_color_gradient(low="yellow",high="blue")
plot(p)
```

`@sample_code`
```{r}
p <-ggplot(diamonds, aes(x=cut, y=carat,color=price))+
  geom_jitter() +
  __________()+
  __________(_______)
plot(p)
```

`@solution`
```{r}
p <-ggplot(diamonds, aes(x=cut, y=carat,color=price))+
  geom_jitter() +
  theme_minimal()+
  scale_color_gradient(low="yellow",high="blue")
plot(p)
```

`@sct`
```{r}
ex() %>% check_error()
ex() %>% check_function("theme_minimal")
fscalecol <- ex() %>% check_function("scale_color_gradient")
fscalecol %>% check_arg("low") %>% check_equal()
fscalecol %>% check_arg("high") %>% check_equal()
success_msg("Bravo! C'est de toute beauté!")
```

---

## Rajout d'un nuage de points montrant les moyennes

```yaml
type: NormalExercise
key: 4afcf79a89
xp: 100
```

`ggplot2`, `dplyr` et `diamonds` ont déjà été chargés.

`@instructions`
**Complétez** le code ci-contre pour rajouter des **points bleus** montrant les **moyennes de prix** (donc moyennes de y) par coupe de diamant

`@hint`


`@pre_exercise_code`
```{r}
library(ggplot2)
library(dplyr)
data(diamonds)
```

`@sample_code`
```{r}
df_moyprix <- diamonds %>%
     .... %>%
     ....

p <- ggplot(diamonds, aes(x=cut, y=price)) +
  geom_boxplot(fill="pink")+
  geom_point(___________)
plot(p)
```

`@solution`
```{r}
df_moyprix <- diamonds %>%
     group_by(cut) %>%
     summarise(moyprix=mean(price))

p <- ggplot(diamonds, aes(x=cut, y=price)) +
  geom_boxplot(fill="pink")+
  geom_point(data=df_moyprix, aes(y=moyprix))
plot(p)
```

`@sct`
```{r}
ex() %>% check_error()

ex() %>% check_function("ggplot")
fgeom <- ex() %>% check_function("geom_point")
fgeom %>% check_arg("data") %>% check_equal()
fgeom %>% check_arg("mapping") %>% check_equal()
fgeom %>% check_arg("col") %>% check_equal()
success_msg("Oui! Visiblement, le prix d'un diamant est peu corrélé à la perfection de sa coupe!")
```

---

## Des facettes par milliers?

```yaml
type: MultipleChoiceExercise
key: 6309643bfd
xp: 50
```

**Examinez** le code suivant (sans l'exécuter!):

```{r}
p <- ggplot(diamonds, aes(x=carat, y=price)) +
  geom_point(aes(color=cut), alpha=0.1)+
  geom_smooth(method="lm", aes(linetype=clarity))
plot(p)
```

Au vu de ces commandes, **combien de droites de régression** s'attendrait-on à voir sur le graphique correspondant?

`@possible_answers`
- 5, autant que de niveaux de `cut`
- 8, autant que de niveaux de `clarity`
- 1, i.e. un modèle global pour l'ensemble des données
- 40, i.e. le nombre de niveaux de `cut` multiplié par le nombre de niveaux de `clarity`

`@hint`
`cut` ne joue que sur le `geom_point()` et non sur le graphique dans son ensemble...

`@pre_exercise_code`
```{r}

```

`@sct`
```{r}
ex()%>%check_mc(correct = 2,
        feedback_msgs = c("Non, `cut` ne joue que sur la couleur des points",
                          "Oui! 8 niveaux, cela fait un graphique déjà bien assez chargé comme ça!!",
                          "Non, `clarity` fait partie des esthétiques de `geom_smooth`.",
                          "Ouhla, non! `cut` ne joue que sur la couleur des points..."))

```
