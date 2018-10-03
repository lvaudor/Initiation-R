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

Le tableau `catdata` et le package `dplyr` ont déjà été chargés dans l'environnement ci-contre.

`@instructions`
Examinez la table `catdata`.
Complétez le code pour sélectionner :

- les variables `weight`, `foodtype`, et `age`
- toutes les variables SAUF `foodtype` et `sex`
- toutes les variables de `haircolor` à `weight`
- toutes les variables qui commencent par le motif `hair`, à l'aide de `starts_with()`

`@hint`
Pour dire "de haircolor à weight", vous pouvez utiliser la notation suivante: `haircolor:weight`.

`@pre_exercise_code`
```{r}
catdata=readr::read_delim("http://perso.ens-lyon.fr/lise.vaudor/Rdata/Graphiques_avec_ggplot2/catdata.csv",sep=";")
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

---

## Filtrer des lignes

```yaml
type: NormalExercise
key: 20ab0a73fc
xp: 100
```

Le tableau `catdata` et le package `dplyr` ont déjà été chargés dans l'environnement ci-contre.


`@instructions`
Examinez la table `catdata`.
Complétez le code pour filtrer les lignes et ne garder que:

`@hint`
Complétez le code pour filtrer les lignes et ne garder que:

- les chats dont le **poil est roux** (`data_roux`)
- les chats **particulièrement gros** (7 kilos ou plus) ou **particulièrement vieux** (15 ans ou plus) (`data_gros_ou_vieux`)

`@pre_exercise_code`
```{r}
catdata=readr::read_delim("http://perso.ens-lyon.fr/lise.vaudor/Rdata/Graphiques_avec_ggplot2/catdata.csv",sep=";")
library(dplyr)
```

`@sample_code`
```{r}
data_roux <- _____
data_roux

data_gros_ou_vieux <- _____
data_gros_ou_vieux
```

`@solution`
```{r}
data_roux <- filter(catdata,haircolor=="red")
data_roux

data_gros_ou_vieux <- filter(catdata, weight>=7 | age>=15)
data_gros_ou_vieux
```

`@sct`
```{r}
ex()%>%check_error()
ex()%>%check_object("data_roux")%>%check_equal()
ex()%>%check_object("data_gros_ou_vieux")%>%check_equal()
success_msg("Bravo! Vous savez maintenant filtrer les lignes d'un jeu de données.")
```

---

## Arranger les lignes

```yaml
type: NormalExercise
key: aa093b5f55
xp: 100
```

La fonction **arrange()** permet de **réordonner** les lignes d'un tableau. 

Le tableau `catdata` et le package `dplyr` ont déjà été chargés dans l'environnement ci-contre.

`@instructions`
Complétez le code pour réarranger les tableaux par 

- **poids**
- **sexe**
- **sexe et âge**
- **sexe** et **âge décroissant**

`@hint`
Pensez à utiliser la fonction auxiliaire `desc()` pour ranger les valeurs dans l'ordre décroissant.

`@pre_exercise_code`
```{r}
catdata=readr::read_delim("http://perso.ens-lyon.fr/lise.vaudor/Rdata/Graphiques_avec_ggplot2/catdata.csv",sep=";")
library(dplyr)
```

`@sample_code`
```{r}
data_par_poids <- arrange(catdata,_____)

data_par_sexe  <- arrange(_____________)

data_par_sexe_et_age <-  _____(_________________)

data_par_sexe_et_age_decr <- ___________________________
```

`@solution`
```{r}
data_par_poids <- arrange(catdata,weight)

data_par_sexe <- arrange(catdata,sex)

data_par_sexe_et_age <- arrange(catdata,sex,age)

data_par_sexe_et_age_decr <- arrange(catdata,sex,desc(age))
```

`@sct`
```{r}
ex()%>%check_error()
ex()%>%check_object("data_par_poids")%>%check_equal()
ex()%>%check_object("data_par_sexe")%>%check_equal()
ex()%>%check_object("data_par_sexe_et_age")%>%check_equal()
ex()%>%check_object("data_par_sexe_et_age_decr")%>%check_equal()
success_msg("Oui! Vous allez pouvoir bien ranger vos données...")
```

---

## Transformer le tableau

```yaml
type: NormalExercise
key: cf99649667
xp: 100
```

La fonction **mutate()** permet de **créer et ajouter de nouvelles variables** à un tableau.

Le tableau `catdata` et les packages `dplyr` et `stringr` ont déjà été chargés dans l'environnement ci-contre.

`@instructions`
Complétez le code pour créer de nouvelles variables:

- dans `data_plus_age_humain`, la nouvelle variable **age_humain** sera l'"âge équivalent humain" du chat (i.e. son âge multiplié par 7).
- dans `data_plus_hair`, la nouvelle variable **hair** correspondra à la couleur et au type de pelage (par exemple, pour un chat "red",et "tabby", `hair` aura pour valeur "red_tabby"). Pour cela, vous pourrez utiliser la fonction `str_c()` du package `stringr` qui concatène des chaînes de caractère.

`@hint`


`@pre_exercise_code`
```{r}
catdata=readr::read_delim("http://perso.ens-lyon.fr/lise.vaudor/Rdata/Graphiques_avec_ggplot2/catdata.csv",sep=";")
library(dplyr)
```

`@sample_code`
```{r}
data_plus_age_humain <- ______________________

# juste pour vous montrer comment fonctionne la fonction `str_c()`
vdemo=c("pouet","coin")
str_c(vdemo,"-",vdemo)

data_plus_hair <- mutate(catdata,hair=_____)
```

`@solution`
```{r}
data_plus_age_humain <- mutate(catdata,age_humain=age*7)

data_plus_hair <- mutate(catdata,hair=paste(haircolor,hairpattern,sep="_"))
```

`@sct`
```{r}
ex()%>%check_error()
ex()%>%check_object("data_plus_hair")%>%check_equal()
ex()%>%check_object("data_plus_age_humain")%>%check_equal()
success_msg("Oui... avez-vous vu le chat qui a 119 ans-humains?")
```
