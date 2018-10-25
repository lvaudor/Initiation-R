---
title: Programmation
description: ""
---

## Structure if

```yaml
type: MultipleChoiceExercise
key: 713f9bb3ca
xp: 50
```

**Examinez** le code suivant (**sans l'exécuter** sinon c'est de la triche!...):

```{r, eval=FALSE}
truc <- 5.2

if(truc<10){
  if(truc>0){
    print("pouet pouet")
  }else{
    print("badaboum")
  }
  if(truc<4){
    print("crac boum hue")
  }else{
    print("kadagwek")
  }
  if(mean(truc)>=5){
    print("woup woup")
  }
}
```

Quel sont les **messages qui s'affichent** dans la console?

`@possible_answers`
- **pouet pouet** puis **crac boum hue**
- **badaboum** puis **crac boum hue** puis **woup woup**
- **pouet pouet** puis **kadagwek** puis **woup woup**
- **pouet pouet** puis **kadagwek**

`@hint`


`@pre_exercise_code`
```{r}

```

`@sct`
```{r}
msg_wrong="Non! Essayez de bien décomposer, dans l'ordre, les instructions..."
msg_right="Oui bravo! Vous commencez à savoir parler R couramment..."
ex() %>% 
  check_mc(correct = 3,
           feedback_msgs = c(msg_wrong,msg_wrong,msg_right,msg_wrong))
```

---

## Ecrire une fonction

```yaml
type: NormalExercise
key: 7a58da9be9
xp: 100
```

Examinez le code ci-contre. Servez-vous de cet exemple pour construire la fonction `create_histogram()` qui prend pour argument d'entrée un nom d'ingrédient de la table `broceliande` (déjà dans l'environnement),

`@instructions`
Servez-vous de cet exemple pour construire la fonction `create_histogram()` qui prend pour argument d'entrée un nom d'ingrédient de la table `broceliande` (déjà dans l'environnement), et renvoie en sortie son histogramme. Testez l'appel à cette fonction sur différentes variables.

`@hint`
Dans le code de la fonction, remplacez le nom de l'objet qu'on veut faire varier par le nom de l'argument!

`@pre_exercise_code`
```{r}
broceliande=read.csv("http://perso.ens-lyon.fr/lise.vaudor/grimoireStat/datasets/broceliande.csv",
                     header=TRUE,sep=";")
```

`@sample_code`
```{r}
library(ggplot2)

p <- ggplot(broceliande,aes_string("perlimpinpin"))+
		geom_histogram(fill="pink")

create_histogram <- function(nomvariable=____){
_____
_____
_____
}

create_histogram("age")
```

`@solution`
```{r}
library(ggplot2)

p <- ggplot(broceliande,aes_string("perlimpinpin"))+
		geom_histogram(fill="pink")

create_histogram <- function(nomvariable){
	p <- ggplot(broceliande,aes_string(nomvariable))+
			geom_histogram(fill="pink")
  return(p)
}

create_histogram("age")
```

`@sct`
```{r}
ex()%>%{
  check_error(.)
  check_function(.,"create_histogram")
}
success_msg("Eh oui! Pour écrire une fonction, il faut bien **distinguer** les objets qui doivent faire office d'**input** et d'**output** dans un code somme toute ordinaire...")
```

---

## Arguments d'une fonction

```yaml
type: MultipleChoiceExercise
key: 25b17af0ff
xp: 50
```

Examinez la fonction suivante:

create_histogram <- function(nomdata,nomvariable,fillcolor="red"){
	p <- ggplot(nomdata,aes_string(nomvariable))+
			geom_histogram(fill=fillcolor)
  return(p)
}

Qu'est-ce que l'appel suivant me renverrait ? (Répondez sans exécuter le code, et en imaginant que le jeu de données `diamonds` est dans l'environnement)

create_histogram(diamonds,"price")

`@possible_answers`
- un histogramme montrant la distribution de la variable `price` du jeu de données `diamonds`, avec par défaut la couleur de remplissage rouge
- un histogramme montrant la distribution de la variable `price` du jeu de données `diamonds`, avec par défaut la couleur de remplissage grise
- une erreur, car il manque des valeurs d'arguments
- une erreur, car on s'est trompé dans les guillemets

`@hint`
Il n'y a pas nécessairement besoin d'appeler la fonction en précisant l'argument `fillcolor` car il a une valeur par défaut. Par ailleurs, l'objet `diamonds` existe, mais pas l'objet `price`...

`@pre_exercise_code`
```{r}

```

`@sct`
```{r}
ex()%>%check_mc(correct = 1,
        feedback_msgs = c("Oui tout a fait! il n'y a pas d'erreur ici, et la couleur par défaut est 'red'",
                          "Non! la fonction est ecrite de sorte que la couleur par defaut est 'red'",
                          "Non! il n'y a pas besoin de preciser la valeur de la couleur de remplissage, car sa valeur est fixee par defaut a 'red'",
                          "Non! l'objet `diamonds` existe dans l'environnement, mais pas l'objet `price`... C'est donc normal que diamonds soit sans guillemets et price avec guillemets..."))
```

---

## Boucle for

```yaml
type: NormalExercise
key: 1e5c33aa90
xp: 100
```

On considère un certain nombres de variables du jeu de données `broceliande` (déjà dans l'environnement). Complétez la boucle for pour produire un histogramme pour chacune des variables listées.

`@instructions`
Complétez la boucle for pour produire un histogramme pour chacune des variables listées.

`@hint`
Il faut que le compteur parcoure le vecteur `variables`.

`@pre_exercise_code`
```{r}
library(ggplot2)
broceliande=read.csv("http://perso.ens-lyon.fr/lise.vaudor/grimoireStat/datasets/broceliande.csv",
                     header=TRUE,sep=";")
create_histogram <- function(nomdata,nomvariable,fillcolor="red"){
	p <- ggplot(nomdata,aes_string(nomvariable))+
			geom_histogram(fill=fillcolor)
  return(p)
}

```

`@sample_code`
```{r}
variables=c("age","hauteur","largeur","perlimpinpin")
for (___){
  p <- create_histogram(___)
  plot(p)
}
```

`@solution`
```{r}
variables=c("age","hauteur","largeur","perlimpinpin")
for (i in 1:length(variables)){
  p <- create_histogram(broceliande,variables[i])
  plot(p)
}
```

`@sct`
```{r}
ex()%>%{
  check_error(.,)
  check_for(.)
  check_code(.,"in")
}
success_msg("Bien joué! Ici à chaque itération l'objet `p` est écrasé de même que le graphique. On va procéder différemment dans l'exercice suivant...")
```

---

## Itération avec purrr

```yaml
type: NormalExercise
key: 4e9e35bc57
xp: 100
```

On cherche à nouveau à automatiser la production d'histogrammes en se servant à la fois de notre fonction `create_histogram()` (un peu modifiée, voir ci-contre) et la fonction `map()` du package `purrr` (déjà chargé dans l'environnement).

`@instructions`
Produisez l'objet listplots puis voyez comment la fonction wrap_plots de patchwork peut utiliser cette liste de plots pour produire un graphique composite.

`@hint`
Avez-vous bien utilisé les arguments dans le bon ordre dans l'appel à la fonction `map()`?

`@pre_exercise_code`
```{r}
library(ggplot2)
library(purrr)
broceliande=read.csv("http://perso.ens-lyon.fr/lise.vaudor/grimoireStat/datasets/broceliande.csv",
                     header=TRUE,sep=";")

```

`@sample_code`
```{r}
create_histogram <- function(nomvariable,nomdata=broceliande,fillcolor="red"){
	p <- ggplot(nomdata,aes_string(nomvariable))+
			geom_histogram(fill=fillcolor)
  return(p)
}
create_histogram("largeur")

variables=c("age","hauteur","largeur","perlimpinpin")
listplots <- map(___________)
patchwork::wrap_plots(listplots)

```

`@solution`
```{r}
create_histogram <- function(nomvariable,nomdata=broceliande,fillcolor="red"){
	p <- ggplot(broceliande,aes_string(nomvariable))+
			geom_histogram(fill=fillcolor)
  return(p)
}
create_histogram("largeur")

variables=c("age","hauteur","largeur","perlimpinpin")
listplots <- map(variables,create_histogram)
patchwork::wrap_plots(listplots)
```

`@sct`
```{r}
ex()%>%{
  check_error(.)
  check_function(.,"map")%>% {
    check_arg(.,".f")
    check_arg(.,".x")}
}

success_msg("Bravo! Avez-vous remarqué que nous avions changé l'ordre des arguments de la fonction `create_histogram()` de façon à ce que le nom de la variable soit le **premier argument?")
```
