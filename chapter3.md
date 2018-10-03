---
title: 'Manipuler des tableaux de données'
description: "Ces exercices visent a vous apprendre a manipuler des tableaux a l'aide du package dplyr.\n\n<a href=\"http://perso.ens-lyon.fr/lise.vaudor/Supports_formation/startR_3_tableaux_de_donnees.html\" target=\"_blank\"> Lien vers les diapos de cours </a>"
---

## Lire une tibble

```yaml
type: NormalExercise
key: 9ad23ac3f2
xp: 100
```

Le tableau **catdata** est **disponible en ligne à l'adresse indiquée dans le script ci-contre**.


`@instructions`
Utilisez la fonction `read_csv()` ou read_delim()` (du package `readr`) pour lire cette table et assignez-la à un objet `catdata`

`@hint`
Avez-vous repéré quel était le séparateur de colonne? il s'agit d'un ";". Dans ce cas mieux vaut utiliser la fonction `read_delim()`...

`@pre_exercise_code`
```{r}

```

`@sample_code`
```{r}
library(readr)
catdata <- ...
catdata
```

`@solution`
```{r}
catdata <- read_delim("http://perso.ens-lyon.fr/lise.vaudor/Rdata/Graphiques_avec_ggplot2/catdata.csv",
                      delim=";")
catdata
```

`@sct`
```{r}
ex()%>%check_error()
ex()%>%check_object("catdata")
success_msg("Oui, bravo! Dans mon fichier catdata.csv, le séparateur de colonnes était un point-virgule, et non une virgule comme attendu par `read_csv()`. Mieux valait donc passer par `read_delim()`")
```

---

## Sélectionner des colonnes

```yaml
type: NormalExercise
key: f6dfa6811a
xp: 100
```

La fonction **select()** permet de **sélectionner des colonnes** d'un tableau de données.

`@instructions`
Le tableau `catdata` et le package `dplyr` ont déjà été chargés dans l'environnement ci-contre.

Complétez le code pour sélectionner :

- les variables `weight`, `foodtype`, et `age`
- toutes les variables SAUF `foodtype` et `sex`
- toutes les variables de `haircolor` à `weight`
- toutes les variables qui commencent par le motif `hair`, à l'aide de `starts_with()`

`@hint`
Pour dire "de haircolor à weight", vous pouvez utiliser la notation suivante: `haircolor:weight`.

`@pre_exercise_code`
```{r}
catdata=read.table("http://perso.ens-lyon.fr/lise.vaudor/Rdata/Graphiques_avec_ggplot2/catdata.csv", sep=";", header=T)
library(dplyr)
```

`@sample_code`
```{r}
#les variables `weight`, `foodtype`, et `age`
dat1 <- select(catdata,_______)
dat1
#toutes les variables SAUF `foodtype` et `sex`
dat2 <- select(_______________)
dat2
#toutes les variables de `haircolor` à `weight`
dat3 <- ______(_______________)
dat3
#toutes les variables qui commencent par le motif `hair`, à l'aide de `starts_with()`
dat4 <- _______________________
dat4
```

`@solution`
```{r}
#les variables `weight`, `foodtype`, et `age`
dat1 <- select(catdata, weight, foodtype, age)
dat1
#toutes les variables SAUF `foodtype` et `sex`
dat2 <- select(catdata, - foodtype, -sex)
dat2
#toutes les variables de `haircolor` à `weight`
dat3 <- select(catdata, haircolor:weight)
dat3
#toutes les variables qui commencent par le motif `hair`, à l'aide de `starts_with()`
dat4 <- select(catdata,starts_with("hair"))
dat4
```

`@sct`
```{r}
ex()%>%check_error()
ex()%>%check_object("dat1")%>%check_equal()
ex()%>%check_object("dat2")%>%check_equal()
ex()%>%check_object("dat3")%>%check_equal()
ex()%>%check_object("dat4")%>%check_equal()
success_msg("C'est ça! Vous avez compris le truc pour sélectionner facilement des variables de votre jeu de données.")
```