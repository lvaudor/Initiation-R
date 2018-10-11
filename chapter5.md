---
title: 'GRAPHIQUES: MAPPING ET FACETTES'
description: 'Mapping et facettes description : Ces exercices visent a vous familiariser avec les principes du mapping et des facettes, en vous permettant de représenter davantage d''information sur vos graphiques'
---

## Mapping

```yaml
type: NormalExercise
key: 8bdf43f60e
xp: 100
```

`ggplot2` et `diamonds` ont déjà été chargés.

`@instructions`
**Complétez** le code ci- contre pour que:

- `p1`, `p2` et `p3` soient trois **nuages de points** représentant le **prix** (`price`) en fonction du **nombre de carats** (`carat`)
- la **couleur** du `geom_point()` de `p1` corresponde à la coupe des diamants (`cut`)
- la **taille** du `geom_point()` de `p2` corresponde à la table des diamants(`table`)
- **les deux conditions précédentes** soient remplies pour le `geom_point()` de `p3`

`@hint`
Avez-vous bien fait appel à la fonction `aes()` dans vos appels à `geom_point()`? 

Cette fonction `aes()` peut prendre plusieurs arguments, séparés par une virgule...

`@pre_exercise_code`
```{r}
require(ggplot2)
data(diamonds)
```

`@sample_code`
```{r}
p1 <- ggplot(diamonds, aes(x=___, y=___)) +
  geom_point(aes(____))
plot(p1)


p2 <- ggplot(________, aes(_____________))+
  geom_point(_________)
plot(p2)


p3 <- ggplot(____________________________)+
   ________(__________)
plot(p3)
```

`@solution`
```{r}
p1 <- ggplot(diamonds, aes(x=carat, y=price)) +
  geom_point(aes(color=cut))
plot(p1)


p2 <- ggplot(diamonds, aes(x=carat, y=price))+
  geom_point(aes(size=table))
plot(p2)


p3 <- ggplot(diamonds, aes(x=carat, y=price))+
  geom_point(aes(size=table, color=cut))
plot(p3)
```

`@sct`
```{r}
ex()%>%check_error()

#fggplot1 <- ex() %>% check_function("ggplot",index=1)
#fggplot1 %>% check_arg("mapping")
ex() %>% {
  check_function(., 'ggplot',index=1) %>% {
      check_arg(., 'data') %>% check_equal()
      check_arg(., 'mapping') %>% check_function('aes') %>% {
        check_arg(., 'x') %>% check_equal(eval = FALSE)
        check_arg(., 'y') %>% check_equal(eval = FALSE)
      }
  }
  check_function(., 'geom_point',index=1)%>%
  {     check_arg(., 'mapping') %>%
           check_function('aes') %>% 
              check_arg(., 'color') %>%
                 check_equal(eval = FALSE)
  }
    check_function(., 'ggplot',index=2) %>% {
      check_arg(., 'data') %>% check_equal()
      check_arg(., 'mapping') %>% check_function('aes') %>% {
        check_arg(., 'x') %>% check_equal(eval = FALSE)
        check_arg(., 'y') %>% check_equal(eval = FALSE)
      }
  }
  check_function(., 'geom_point',index=2)%>%
  {     check_arg(., 'mapping') %>%
           check_function('aes') %>% 
              check_arg(., 'size') %>%
                 check_equal(eval = FALSE)
  }
    check_function(., 'ggplot',index=3) %>% {
      check_arg(., 'data') %>% check_equal()
      check_arg(., 'mapping') %>% check_function('aes') %>% {
        check_arg(., 'x') %>% check_equal(eval = FALSE)
        check_arg(., 'y') %>% check_equal(eval = FALSE)
      }
  }
  check_function(., 'geom_point',index=3)%>%
  {     check_arg(., 'mapping') %>%
           check_function('aes') %>% {
              check_arg(., 'color') %>%
                 check_equal(eval = FALSE)
              check_arg(.,'size')%>%
                 check_equal(eval=FALSE)
           }
  }
  check_error(.)
}

success_msg("Très bien! En faisant du **mapping** vous ajoutez des informations supplémentaires à votre graphique uni ou bivarié...")
```

---

## Paramètres fixes vs paramètres variables

```yaml
type: NormalExercise
key: ecda72717f
xp: 100
```

`ggplot2` et `diamonds` ont déjà été chargés. On reprend le dernier graphique créé, `p3`.

`@instructions`
**Modifiez** le code ci-contre pour que la **forme** des points corresponde à un **carré plein** (voir l'antisèche ggplot2...)

`@hint`
Si vous définissez le paramètre comme une **constante**, vous devez le spécifier à l'**extérieur** de la fonction `aes()`...

`@pre_exercise_code`
```{r}
library(ggplot2)
data(diamonds)
```

`@sample_code`
```{r}
p3 <- ggplot(diamonds, aes(x=carat, y=price))+
  geom_point(aes(size=table, color=cut))
plot(p3)
```

`@solution`
```{r}
p3 <- ggplot(diamonds, aes(x=carat, y=price))+
  geom_point(shape=15, aes(size=table, color=cut))
plot(p3)
```

`@sct`
```{r}
ex()%>%{
  check_function(., 'ggplot') %>% {
      check_arg(., 'data') %>% check_equal()
      check_arg(., 'mapping') %>% check_function('aes') %>% {
        check_arg(., 'x') %>% check_equal(eval = FALSE)
        check_arg(., 'y') %>% check_equal(eval = FALSE)
      }
  }
    check_function(., 'geom_point')%>%
  {     check_arg(., 'mapping') %>%
           check_function('aes') %>%{ 
              check_arg(., 'color') %>%
                 check_equal(eval = FALSE)
              check_arg(., 'size') %>%
                 check_equal(eval = FALSE)
             }
  }
  check_error()
}  

success_msg("Oui! Vous pouvez soit définir les paramètres des geoms comme des constantes, ou bien les relier à des variables via le processus de mapping...")

```

---

## Esthétique globale ou propre à un geom

```yaml
type: MultipleChoiceExercise
key: 0bb9a00d4a
xp: 50
```

Considérez les lignes de codes suivantes:

```{r}
p <- ggplot(diamonds, aes(x=cut, y=carat, color=cut))+
  geom_boxplot(fill="grey") +
  geom_rug()
plot(p)
```

Quelle proposition est **vraie**?

`@possible_answers`
- la **couleur de remplissage** des boxplots dépend de `cut`
- la **couleur** des "rugs" est grise
- la **couleur de bordure** des boxplots est grise
- la **couleur de remplissage** des boxplots est grise

`@hint`
Portez attention à l'endroit où sont définies les esthétiques (dans `ggplot()` ou dans un `geom_xxx()`?) et au paramètre considéré (couleur de bordure `color` ou couleur de remplissage `fill`?)

`@pre_exercise_code`
```{r}

```

`@sct`
```{r}
ex()%>%check_mc(correct = 4,
        feedback_msgs = c("Non, c'est la couleur de **bordure** des boxplots qui dépend de `cut`",
                          "Non, la couleur des rugs dépend de `cut`!",
                          "Non, la couleur de bordure des boxplots dépend de `cut`...",
                          "Oui, bravo! Les paramètres renseignés **dans l'appel à `ggplot()`** valent pour l'**ensemble** des geoms..."))
```

---

## Ajustement de la position

```yaml
type: NormalExercise
key: e85eacef8b
xp: 100
```

`ggplot2` et `diamonds` ont déjà été chargés.

`@instructions`
Examinez le code ci-contre et le graphique qu'il renvoie.

**Corrigez** ce code pour que les effectifs des différentes coupes apparaissent les **uns à côté des autres** (paramètre `position`... consultez votre antisèche!!)

`@hint`
Le paramètre de position **n'est pas** une esthétique.

Vous pouvez voir les valeurs possibles pour ce paramètre sur votre **antisèche ggplot** (2ème page, "Position Adjustments")

`@pre_exercise_code`
```{r}
library(ggplot2)
data(diamonds)
```

`@sample_code`
```{r}
p <- ggplot(diamonds, aes(x=carat))+
  geom_histogram(bins=10,aes(fill=cut))
plot(p)
```

`@solution`
```{r}
p <- ggplot(diamonds, aes(x=carat))+
  geom_histogram(bins=10, position="dodge",aes(fill=cut))
plot(p)
```

`@sct`
```{r}
ex()%>%{
  check_function(., 'ggplot') %>% {
      check_arg(., 'data') %>% check_equal()
      check_arg(., 'mapping') %>% check_function('aes') %>% {
        check_arg(., 'x') %>% check_equal(eval = FALSE)
      }
  }
   check_function(., 'geom_histogram')%>%
  {     check_arg(., 'mapping') %>%
           check_function('aes') %>%{ 
              check_arg(., 'fill') %>%
                 check_equal(eval = FALSE)
             
           }
        check_arg(.,"position")%>%check_equal()
  }
  check_error(.)
}  

success_msg("Oui! Avez-vous pris le temps pour bien comprendre comment le paramètre `position` modifiait la façon dont on peut lire le graphique?")

```

---

## Facettes

```yaml
type: NormalExercise
key: 1da53fccda
xp: 100
```

`ggplot2` et `diamonds` ont déjà été chargés.

`@instructions`
**Complétez** le code ci-contre pour produire **différentes facettes** du même graphique **en fonction de la coupe** des diamants (**5 lignes, 1 colonne**)

`@hint`
Avez-vous bien fait en sorte que les facettes soient **en ligne** et non **en colonne** dans l'appel à la fonction `facet_grid()`?

`@pre_exercise_code`
```{r}
require(ggplot2)
data(diamonds)
```

`@sample_code`
```{r}
p <- ggplot(diamonds, aes(x=carat, y=price, color=cut)) +
  geom_point() +
  ____________
plot(p)
```

`@solution`
```{r}
p <- ggplot(diamonds, aes(x=carat, y=price, color=cut)) +
  geom_point() +
  facet_grid(rows=vars(cut))
plot(p)
```

`@sct`
```{r}
ex()%>%{
  check_function(., 'ggplot') %>% {
      check_arg(., 'data') %>% check_equal()
      check_arg(., 'mapping') %>% check_function('aes') %>% {
        check_arg(., 'x') %>% check_equal(eval = FALSE)
        check_arg(., 'y') %>% check_equal(eval = FALSE)
        check_arg(., 'color') %>% check_equal(eval = FALSE)
      }
  }
  check_function(., 'geom_point')
  check_function(.,'facet_grid')%>% 
  {     check_arg(., 'rows') %>%
           check_function('vars') %>%{ 
              check_arg(.,'...') %>%
                 check_equal(eval = FALSE)             
           }
  }
  check_error(.)
}  

success_msg("Eh oui, bien joué! Les facettes , c'est trop de la boule :-) !")
```
