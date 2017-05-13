
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

O levantamento destas informações adicionais (metadados) será feito com uso de funções específicas disponívei nativamente no R. Por exemplo, para a descoberta da dimensão do dataset iris, deve-se usar a função dim() cujo argumento é a base de dados. 

```{r}
# verificar a dimensão do dataset iris
# atribua o resusltado da dimensão na varipável d
```

*** =solution
```{r}
d <- dim(iris)
```

*** =sct
```{r}
test_error()
test_object("d",
            undefined_msg = "Tenha certeza de que a variável  `d` foi definida! ",
            incorrect_msg = "Você atribuiu o resultado da função dim() a variável `d`!")
success_msg("Good job! Vamos continuar fazendo a análise exploratória dos dados")

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