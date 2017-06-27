---
title       : Criação de metadados sobre um dataset
description : Este capitulo consiste em analisar um dataset para fazer descobertas sobre o dataset com a finalidade de conhecer o mesmo. O resultado destas análise é uma série de informações que podem ser usadas a porteiori para dicidir sobre os tipos de pré-processamentos necessários e também os tipos de algoritmos de aprendizagem de máquina são mais adequados para uso. A este resultado chamaremos de <b>metadados</b>.


--- type:NormalExercise lang:r xp:100 skills:1 key:427f7df944
## Análise Exploratória de Dados

O exercício consiste em carregar um dataset e fazer algumas explorações iniciais sobre o mesmo com a finalidade de conhecer melhor os dados que serão analisados.

O dataset utilizado neste exercício chama-se Iris, o qual consiste de um tipo de planta descrita por quatro atributos descritivos (largura de sépala, largura de pétala, comprimeto de sépala e comprimeto de pétala) e um atributo classificiatório que pode ser definido em 3 categorias de espécies.

Este é um dataset disponível no repositório do Datacamp e, portanto não é necessário a carga de dados. O carregamento é feito com o uso de uma função chamada *data()*, tendo como argumento o nome do dataset, nesse caso, iris.

Após o carregamento dos dados, a visualização dos mesmos e futuras manipulações podem ser obtidas com o uso do nome *iris*.

Com o dataset carregado procura-se então enriquecer as informações do mesmo como a descoberta da dimensão (número de linhas - exemplares e colunas - atributos), o nome dos atributos, a estrutura e tipos dos atributos.

O levantamento destas informações adicionais, chamado aqui de metadados, será feito com uso de funções específicas disponívei nativamente no R. Por exemplo, para a descoberta da dimensão do dataset iris, deve-se usar a função *dim()* cujo parãmetro é o nome do dataset. 



*** =instructions
a função *dim()* espera receber como parâmetro o nome do dataset

*** =hint
data("iris")

*** =pre_exercise_code
```{r}
data("iris")

```

*** =sample_code
```{r}
# verificar a dimensão do dataset iris
# atribuir o resusltado da dimensão a variável d
```

*** =solution
```{r}
d <- dim(iris)
```

*** =sct
```{r}
test_error()
test_object("d",
            undefined_msg = "Verifique se a variável  `d` foi definida! ",
            incorrect_msg = "Verifique se foi atribuída  a variável `d` o resultado da função `dim()` !")
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
msg1 = "Tente novamente! Caso precise, use *print()* e o nome da variável como argumento dessa função para obter as informações solicitadas."
msg2 = "Well done. Vamos continuar fazendo a análise exploratória dos dados"
msg3 = "Consulte a documentação e tente novamente: https://www.rdocumentation.org/packages/base/versions/3.0.3/topics/dim."
msg4 = "Consulte a documentação e tente novamente: https://www.rdocumentation.org/packages/base/versions/3.0.3/topics/dim."
test_mc(correct = 2, feedback_msgs = c(msg1,msg2,msg3,msg4))
```

--- type:NormalExercise lang:r xp:100 skills:1 key:850307365a
## Conhecendo os atributos do dataset **iris**

Este exercício consiste em carregar um dataset e fazer explorações para a descoberta sobre os atributos do mesmo.


*** =instructions

A descoberta deste metadados (e dos próximos também) será feita com uso de funções específicas disponívei nativamente no R. Por exemplo, para a descoberta da dimensão do dataset iris deve-se usar a função *names()* com parâmetro o nome da variável que contém o dataset carregado, nesse caso do exercício, o próprio nome do dataset. 


*** =hint
data("iris")

*** =pre_exercise_code
```{r}
data("iris")

```

*** =sample_code
```{r}
# verificar o nome dos atributos do dataset iris
# atribuir o resultado com o nome dos atributos à variável n

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
            undefined_msg = "Verifique se a variável  `n` foi definida! ",
            incorrect_msg = "Verifique se foi atribuido a variável `n` o resultado da função `names()` !")
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
Para visualizar o resultado de uma variável use a função *print()*

*** =pre_exercise_code
```{r}
# no pec
```

*** =sct
```{r}
msg1 = "Consulte a documentação e tente novamente: https://www.rdocumentation.org/packages/base/versions/3.0.3/topics/names."
msg2 = "Tente novamente! Caso precise, use a função  *print()* com argumento o nome da variável que recebe o resultado da dimensão."
msg3 = "Tente novamente! Caso precise, use a função  *print()* com argumento o nome da variável que recebe o resultado da dimensão."
msg4 = "Well done. Vamos continuar fazendo a análise exploratória dos dados"
test_mc(correct = 4, feedback_msgs = c(msg1,msg2,msg3,msg4))
```

--- type:NormalExercise lang:r xp:100 skills:1 key:5cb0c44603
## Conhecendo os atributos do dataset *iris*

Em continuidade aos exercícios de explorações iniciais, o desafio aqui é descobrir sobre a estrutura do dataset.


*** =instructions

A descoberta da estrutura do dataset para o levantamento das informações adicionais (metadados) será feito com uso da função *str()* cujo parâmetro é o nome do dataset (ou da variável usada para armazenar o dataset). O resultado do uso desta função é a dimensão do dataset, o nome dos atributos, o tipo dos atributos e uma amostra dos valores de cada variável.


*** =hint
data("iris")

*** =pre_exercise_code
```{r}
data("iris")

```

*** =sample_code
```{r}
# verificar a estrtura do dataset iris
# atribuir o resultado da estrtura a variável s


```

*** =solution
```{r}
s <- str(iris)
```

*** =sct
```{r}
test_error()
test_object("s",
            undefined_msg = "Verifique se a variável  `s` foi definida! ",
            incorrect_msg = "Verifique se atribuiu a variável `s` o resultado da função `str()` !")
success_msg("Good job! Vamos continuar fazendo a análise exploratória dos dados")

```
---

--- type:MultipleChoiceExercise lang:r xp:50 skills:3 key:43ef61a87b
## Em relação aos do dataset iris:

Quais os tipos dos atributos?

*** =instructions
- 3 numéricos (num) e 1 categórico (factor)
- 1 numérico (num) e 3 categóricos (factor)
- 4 numéricos (num) e 1 categórico (factor)
- apenas atributos numéricos

*** =hint
Para visualizar o resultado de uma variável, use a função *print()*

*** =pre_exercise_code
```{r}
# no pec
```

*** =sct
```{r}
msg1 = "Tente novamente! Caso precise, use a função  *print()* com argumento o nome da variável que recebe o resultado da estrutura."
msg2 = "Tente novamente! Caso precise, use a função  *print()* com argumento o nome da variável que recebe o resultado da estrutura."
msg3 = "Well done. Vamos continuar fazendo a análise exploratória dos dados"
msg4 = "Tente novamente! Caso precise, use a função  *print()* na variável que recebe o resultado da estrtura para obter estas informações."
test_mc(correct = 3, feedback_msgs = c(msg1,msg2,msg3,msg4))
```

--- type:NormalExercise lang:r xp:100 skills:1 key:a773fcb8e3
## Conhecendo os atributos do dataset iris

Este exercício consiste em carregar um dataset e fazer algumas explorações iniciais sobre os mesmos


*** =instructions

O levantamento destas informações adicionais (metadados) será feito com uso de funções específicas disponívei nativamente no R. Por exemplo, para a descoberta da dimensão do dataset iris, deve-se usar a função *summary()* cujo argumento é a base de dados. 


*** =hint
data("iris")

*** =pre_exercise_code
```{r}
data("iris")

```

*** =sample_code
```{r}
# verificar o nome dos atributos dataset iris
# atribua o resusltado dos nomes na variável su



#print()


```

*** =solution
```{r}
sm <- summary(iris)
```

*** =sct
```{r}
test_error()
test_object("sm",
            undefined_msg = "Verifique se a variável  `sm` foi definida! ",
            incorrect_msg = "Verifique se atribuiu a variável `sm` o resultado da função `summary()` !")
success_msg("Good job! Vamos continuar fazendo a análise exploratória dos dados")

```
---


--- type:MultipleChoiceExercise lang:r xp:50 skills:3 key:536782eac4
## Em relação aos resultados da função summary:

Qual o resulatdo a função apresenta?

*** =instructions
- apresentação resumida dos exemplares do dataset
- um resumo estatístico do dataset
- alguns exemplos de valores dos atributos
- a função não tem retorno de valor

*** =hint
Para visualizar o resultado de uma variável, use a função *print()*

*** =pre_exercise_code
```{r}
# no pec
```

*** =sct
```{r}
msg1 = "Consulte a documentação e tente novamente: https://www.rdocumentation.org/packages/base/versions/3.0.3/topics/summary."
msg2 = "Well done. Vamos continuar fazendo a análise exploratória dos dados"
msg3 = "Consulte a documentação e tente novamente: https://www.rdocumentation.org/packages/base/versions/3.0.3/topics/summary."
msg4 = "Consulte a documentação e tente novamente: https://www.rdocumentation.org/packages/base/versions/3.0.3/topics/summary."
test_mc(correct = 2, feedback_msgs = c(msg1,msg2,msg3,msg4))
```
