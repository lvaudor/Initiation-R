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
