
--- type:NormalExercise lang:r xp:100 skills:1 key:427f7df944
## Análise Exploratória de Dados

Este exercício consiste em carregar um dataset e fazer algumas explorações iniciais sobre os mesmos



*** =instructions
O dataset que será usado neste exercício chama-se iris, o qual consiste de um tipo de planta com 3 categorias de espécies.

Esta é uma base de dados que já existe no repositório do datacamp. O carregamento da base será feito com o uso de uma função chamada data, tendo como argumento o nome do dataset iris.

Para a manipulação dos dados deste dataset deve-se chamar pelo nome *iris*

*** =hint
data("iris")

*** =pre_exercise_code
```{r}
data("iris")

```

*** =sample_code

Com o dataset carregado procura-se então enriquecer as informações com a verificação da dimensão do dataset e conhecimentos sobre os atributos como nome, estrutura e tipos.



```{r}
#print(iris)
```

*** =solution
```{r}
x<-iris["Sepal.Length"]
```

*** =sct
```{r}
test_error()
test_object("x",
            undefined_msg = "Make sure to define `x`!",
            incorrect_msg = "Have you correctly assigned 5 to `x`!")
success_msg("Good job! Head over to the next exercise")

```
---



--- type:MultipleChoiceExercise lang:r xp:50 skills:3 key:e74c30a746
## Multiple Choice Exercise Title

This is the assignment.
How much is `2 + 2`?

*** =instructions
- 2
- 3
- 4

*** =hint
Here's a hint: think about your time in primary school.

*** =pre_exercise_code
```{r}
# no pec
```

*** =sct
```{r}
msg1 = "Try again! Think about your time in school."
msg2 = "Summing two even numbers always leads to another even number. Try again."
msg3 = "Well done. Proceed to the next exercise"
test_mc(correct = 3, feedback_msgs = c(msg1,msg2,msg3))
```