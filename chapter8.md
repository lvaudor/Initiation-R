---
title: 'Tests statistiques'
description: ""
---

## Réalisation d'un test statistique

```yaml
type: NormalExercise
key: 47f3c284e0
xp: 100
```

L'environnement contient le jeu de données `broceliande` et les packages `dplyr` et `infer` ont déjà été chargés.

`@instructions`
Testez le lien entre la variable `enchantement` et la variable `perlimpinpin` pour les deux sous-jeu de données `broceliande_sapins` et `broceliande_chenes`, de manière à obtenir un tableau montrant (entre autres éléments) la valeur de statistique observée, et la p-value.

`@hint`
Avez-vous bien précisé l'argument `order`?

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

test_sapins <- broceliande_sapins %>% 
  ___(___)
test_chenes <- broceliande_chenes %>% 
  ___(___)
```

`@solution`
```{r}
broceliande_sapins=filter(broceliande, espece=="sapin")
broceliande_chenes=filter(broceliande, espece=="chene")

test_sapins <- broceliande_sapins %>% 
  t_test(perlimpinpin~enchantement, order=c(FALSE, TRUE))

test_chenes <- broceliande_chenes %>% 
  t_test(perlimpinpin~enchantement, order=c(FALSE, TRUE))
```

`@sct`
```{r}
ex()%>%{
  check_object(broceliande_sapins)
  check_object(broceliande_chenes)
  check_function(.,'t_test', index=1) %>%check_argument('order') 
  check_function(.,'t_test', index=2) %>%check_argument('order')
  check_error(.)
}  

```

---

## Interprétation d'un test statistique

```yaml
type: MultipleChoiceExercise
key: 6cfedee86a
xp: 50
```

Vous pouvez examiner les objets `test_sapins` et `test_chenes` créés précédemment dans la console ci-contre.

Existe-t-il un lien significatif (au seuil de 5%) entre l'enchantement de l'arbre et la quantité de poudre de perlimpinpin qu'on y retrouve?

`@possible_answers`
- non, pour aucune des espèces
- oui, pour les deux espèces
- oui pour les sapins, non pour les chênes
- non pour les sapins, oui pour les chênes

`@hint`
Il s'agit d'examiner (et de savoir interpréter) la valeur de la p-value!

`@pre_exercise_code`
```{r}
library(dplyr)
library(infer)
broceliande=read.csv("http://perso.ens-lyon.fr/lise.vaudor/grimoireStat/datasets/broceliande.csv",
                     header=TRUE,sep=";")

broceliande_sapins=filter(broceliande, espece=="sapin")
broceliande_chenes=filter(broceliande, espece=="chene")

test_sapins <- broceliande_sapins %>% 
  t_test(perlimpinpin~enchantement, order=c(FALSE, TRUE))

test_chenes <- broceliande_chenes %>% 
  t_test(perlimpinpin~enchantement, order=c(FALSE, TRUE))
```

`@sct`
```{r}
ex()%>%check_mc(correct = 4,
        feedback_msgs = c("On considère un seuil de 5% -0.05- pour décider si on rejette l'hypothèse nulle ou pas",
                          "On considère un seuil de 5% -0.05- pour décider si on rejette l'hypothèse nulle ou pas",
                          "Non! c'est significatif si on REJETTE l'hypothèse nulle, et on rejette l'hypothèse nulle si la p-value est petite",
                          "Oui, bravo! Une p-value petite nous amène à rejeter à l'hypothèse nulle, selon laquelle l'enchantement n'aurait pas d'effet sur la quantité de poudre de perlimpinpin"))
```

---

## Distribution théorique vs simulations

```yaml
type: NormalExercise
key: 4601e30249
xp: 100
```

Repartons du test sur les sapins. Le graphique ci-contre vous montre que l'**hypothèse de normalité** des données n'est peut-être pas respectée... 

Le jeu de données `broceliande_sapins` et le test `test_sapins` réalisés précédemment sont déjà dans l'environnement ci-contre. La librairie `infer` a déjà été chargée.

`@instructions`
Examinons si la distribution de la statistique T obtenue par des simulations serait très différente de la distribution théorique (et si, en conséquence, la p-value donnerait un résultat différent).

Pour cela, créez l'objet `sim_sapins` qui va nous permettre d'observer la distribution **empirique** de la statistique T sous hypothèse d'indépendance (distribution calculée en réalisant des permutations du jeu de données initial).

`@hint`
La valeur de statistique observée est toujours la même, qu'on soit en train de considérer la distribution théorique ou les simulations!

`@pre_exercise_code`
```{r}
broceliande=read.csv("http://perso.ens-lyon.fr/lise.vaudor/grimoireStat/datasets/broceliande.csv",
                     header=TRUE,sep=";")
library(infer)
library(dplyr)
library(ggplot2)
broceliande_sapins=dplyr::filter(broceliande, espece=="sapin")
test_sapins <- broceliande_sapins %>% 
  t_test(perlimpinpin~enchantement, order=c(FALSE, TRUE))

ggplot(broceliande_sapins, aes(x=enchantement,y=perlimpinpin))+
  geom_boxplot()+ 
  geom_point(data=broceliande_sapins %>%
               group_by(enchantement) %>%
               summarise(perlimpinpin=mean(perlimpinpin)),
             col="red")
```

`@sample_code`
```{r}
sim_sapins <- broceliande_sapins %>% 
  ___(perlimpinpin~enchantement) %>%
  ___(null="independence") %>% 
  ___(reps=1000) %>% 
  ___(stat="t", order=c(FALSE,TRUE))

p_value_ancienne <- test_sapins$p_value
obs_stat <- test_sapins$___

p_value_nouvelle <- sim_sapins %>% 
   get_pvalue(obs_stat=___,
              direction="two_sided")

sim_sapins%>%
   visualize(obs_stat=obs_stat,
             direction="two_sided")

# Est-ce que l'interprétation du test est différente si on ne considère pas la distribution théorique de la statistique, 
# mais celle qu'on a calculée sur les données simulées?
# (Répondre "oui" ou "non":)
reponse <- "___"
```

`@solution`
```{r}
sim_sapins <- broceliande_sapins %>% 
  specify(perlimpinpin~enchantement) %>%
  hypothesize(null="independence") %>% 
  generate(reps=1000) %>% 
  calculate(stat="t", order=c(FALSE,TRUE))

p_value_ancienne <- test_sapins$p_value
obs_stat <- test_sapins$statistic

p_value_nouvelle <- sim_sapins %>% 
   get_pvalue(obs_stat=obs_stat,
              direction="two_sided")

sim_sapins%>%
   visualize(obs_stat=obs_stat,
             direction="two_sided")

reponse <- "non"
```

`@sct`
```{r}
ex()%>%{
  check_function(.,"specify")
  check_function(.,"hypothesize")
  check_function(.,"generate")
  check_function(.,"calculate")
  check_object(.,"obs_stat") %>% check_equal()
  check_object(.,"p_value_nouvelle") %>% check_equal()
  check_function(.,"visualize") %>% check_argument("obs_stat") %>% check_value()
  check_object(.,"reponse")%>% check_value()
  check_error(.)
}
```
