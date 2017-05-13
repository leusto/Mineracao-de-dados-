---
title       : Criação de metadados sobre o dataset
description : Este capitulo consiste em ....


--- type:NormalExercise lang:r xp:100 skills:1 key:427f7df944
## Análise Exploratória de Dados

Este exercício consiste em carregar um dataset e fazer algumas explorações iniciais sobre os mesmos



*** =instructions
O dataset que será usado neste exercício chama-se iris, o qual consiste de um tipo de planta com 3 categorias de espécies.

Esta é uma base de dados que já existe no repositório do datacamp. O carregamento da base será feito com o uso de uma função chamada data, tendo como argumento o nome do dataset iris.

Para a manipulação dos dados deste dataset deve-se chamar pelo nome *iris*.

Com o dataset carregado procura-se então enriquecer as informações com a verificação da dimensão do dataset e conhecimentos sobre os atributos como nome, estrutura e tipos.

O levantamento destas informações adicionais (metadados) será feito com uso de funções específicas disponívei nativamente no R. Por exemplo, para a descoberta da dimensão do dataset iris, deve-se usar a função *dim()* cujo argumento é a base de dados. 


*** =hint
data("iris")

*** =pre_exercise_code
```{r}
data("iris")

```

*** =sample_code
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
            undefined_msg = "Tem certeza de que a variável  `d` foi definida! ",
            incorrect_msg = "Tem certeza que atribuiu a variável `d` o resultado da função `dim()` !")
success_msg("Good job! Vamos continuar fazendo a análise exploratória dos dados")

```
---


--- type:MultipleChoiceExercise lang:r xp:50 skills:3 key:e74c30a746
## Em relação a dimensão do dataset iris:

Qual o número de exemplares e o número de atributos presentes no dataset?

*** =instructions
- 5 exemplares e 150 atributos
- 150 exemplares e 5 atributos
- 150 exemplares e 1 atributo
- 5 exemplares e 150 atributos

*** =hint
Para visualizar o resultado de uma variável, use a função *print()*

*** =pre_exercise_code
```{r}
# no pec
```

*** =sct
```{r}
msg1 = "Tente novamente! Caso precise, use a função  *print()* na variável que recebe o resultado da dimensão para obter estas informações."
msg2 = "Well done. Vamos continuar fazendo a análise exploratória dos dados"
msg3 = "Consulte a documentação e tente novamente: https://www.rdocumentation.org/packages/base/versions/3.0.3/topics/dim."
msg4 = "Consulte a documentação e tente novamente: https://www.rdocumentation.org/packages/base/versions/3.0.3/topics/dim."
test_mc(correct = 2, feedback_msgs = c(msg1,msg2,msg3,msg4))
```

--- type:NormalExercise lang:r xp:100 skills:1 key:850307365a
## Conhecendo os atributos do dataset **iris**

Este exercício consiste em carregar um dataset e fazer algumas explorações iniciais sobre os mesmos


*** =instructions

O levantamento destas informações adicionais (metadados) será feito com uso de funções específicas disponívei nativamente no R. Por exemplo, para a descoberta da dimensão do dataset iris, deve-se usar a função *names()* cujo argumento é a base de dados. 


*** =hint
data("iris")

*** =pre_exercise_code
```{r}
data("iris")

```

*** =sample_code
```{r}
# verificar o nome dos atributos dataset iris
# atribua o resusltado dos nomes na varipável n

# para visualziar o valor da variável, use a função print()
```

*** =solution
```{r}
n <- names(iris)
```

*** =sct
```{r}
test_error()
test_object("n",
            undefined_msg = "Tem certeza de que a variável  `n` foi definida! ",
            incorrect_msg = "Tem certeza que atribuiu a variável `n` o resultado da função `names()` !")
success_msg("Good job! Vamos continuar fazendo a análise exploratória dos dados")

```
---


--- type:MultipleChoiceExercise lang:r xp:50 skills:3 key:5623f9558f
## Em relação aos atributos do dataset iris:

Qual o nome dos atributos?

*** =instructions
- 1, 2, 3, 4 e 5
- "Sepal Length","Sepal Width","Petal Length","Petal Width" e "Species"
- "SL","SW","PL","PW" e "Species"
- "Sepal.Length","Sepal.Width","Petal.Length","Petal.Width" e "Species"

*** =hint
Para visualizar o resultado de uma variável, use a função *print()*

*** =pre_exercise_code
```{r}
# no pec
```

*** =sct
```{r}
msg1 = "Consulte a documentação e tente novamente: https://www.rdocumentation.org/packages/base/versions/3.0.3/topics/names."
msg2 = "Tente novamente! Caso precise, use a função  *print()* na variável que recebe o resultado da dimensão para obter estas informações."
msg3 = "Tente novamente! Caso precise, use a função  *print()* na variável que recebe o resultado da dimensão para obter estas informações."
msg4 = "Well done. Vamos continuar fazendo a análise exploratória dos dados"
test_mc(correct = 4, feedback_msgs = c(msg1,msg2,msg3,msg4))
```

--- type:NormalExercise lang:r xp:100 skills:1 key:5cb0c44603
## Conhecendo os atributos do dataset ***iris***

Este exercício consiste em carregar um dataset e fazer algumas explorações iniciais sobre os mesmos


*** =instructions

O levantamento destas informações adicionais (metadados) será feito com uso de funções específicas disponívei nativamente no R. Por exemplo, para a descoberta da dimensão do dataset iris, deve-se usar a função *str()* cujo argumento é a base de dados. 


*** =hint
data("iris")

*** =pre_exercise_code
```{r}
data("iris")

```

*** =sample_code
```{r}
# verificar o nome dos atributos dataset iris
# atribua o resusltado dos nomes na variável s

# para visualziar o valor da variável, use a função print()
```

*** =solution
```{r}
s <- str(iris)
```

*** =sct
```{r}
test_error()
test_object("s",
            undefined_msg = "Tem certeza de que a variável  `s` foi definida! ",
            incorrect_msg = "Tem certeza que atribuiu a variável `s` o resultado da função `str()` !")
success_msg("Good job! Vamos continuar fazendo a análise exploratória dos dados")

```
---
