---
title: 'Tests statistiques'
description: ""
---

## t-test : réalisation du test sous R

```yaml
type: NormalExercise
key: 47f3c284e0
xp: 100
```



`@instructions`


`@hint`


`@pre_exercise_code`
```{r}
library(dplyr)
library(infer)
broceliande=read.csv("http://perso.ens-lyon.fr/lise.vaudor/grimoireStat/datasets/broceliande.csv",
                     header=TRUE,sep=";")
```

`@sample_code`
```{r}
broceliande_sapins=filter(broceliande, espece=="sapin")
broceliande_chenes=filter(broceliande, espece=="chene")

broceliande_sapins %>% 
  t_test(___)

broceliande_chenes %>% 
  t_test(___)
```

`@solution`
```{r}
broceliande_sapins=filter(broceliande, espece=="sapin")
broceliande_chenes=filter(broceliande, espece=="chene")

broceliande_sapins %>% 
  t_test(perlimpinpin~enchantement, order=c(FALSE, TRUE))

broceliande_chenes %>% 
  t_test(perlimpinpin~enchantement, order=c(FALSE, TRUE))
```

`@sct`
```{r}

```
