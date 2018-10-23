---
title: 'Projets et rapports'
description: ""
---

## Insert exercise title here

```yaml
type: MultipleChoiceExercise
key: d16a3e7697
xp: 50
```

Pas facile de vous faire faire un exercice sur la **production semi-automatique de rapports** (de **.Rmd** vers **.docx**, **.html**, ou **.pdf**) depuis la plateforme Datacamp... 

Néanmoins, une question à choix multiple, ça le fait à tous les coups...

Laquelle de ces propositions est **vraie**?

`@possible_answers`
- Vous n'avez pas très très bien compris l'intérêt de la production de rapports depuis RStudio, ça ressemble à une lubie de la prof.
- La production de rapports depuis RStudio est vraiment un aspect intéressant et vous êtes sûr(e) de l'expérimenter très prochainement.
- Vous n'êtes pas sûr(e) d'utiliser la production de rapports depuis RStudio parce que franchement, si vous réussissez déjà à faire tourner deux-trois scripts de base après un seul jour de formation, ça sera déjà pas mal.

`@hint`
Il faut donner la réponse qui fera plaisir à la prof.

`@pre_exercise_code`
```{r}

```

`@sct`
```{r}
ex()%>%check_mc(correct = 2,
        feedback_msgs = c("Non! La prof n'a pas de lubies (si ce n'est l'utilisation intempestive des chats pour illustrer tout et n'importe quoi)...",
                          "Oui! Vous êtes vraiment un(e) petit(e) malin(e)...",
                          "Mais si... Vous allez y arriver!"))
```
