title       : Manipulação sobre o dataset
description : Este capitulo consiste em ....

- selecionar uma variavel
- calcular a media, desvio de uma variavel

- boxplot
- outlier

- grafico de dispersao

- gráfico de histograma




--- type:NormalExercise lang:r xp:100 skills:1 key:66f49495b2
## Selecionando um único atributo do dataset

A seleção de um único atributo do dataset pode ser feito agrupando o nome do dataset ao nome do atributo de interesse. O operador de agrupamento no R  é o <b>$</b>.

Neste desafio pede-se que selecione o atributo <b>Sepal.Length</b>

*** =instructions
<ul>
Lembrando que:
 <li>Para saber o nome dos atributos do dataset usa-se a função <span stype="text-ident:itali,backgroung:#e6f5ff">names()</span></li>
 <li>A seleção de um atributo pode ser feita da seguinte maneira: <span stype="text-ident:itali,backgroung:#e6f5ff">dataset<b>$atributo<b></span></li>
 <li> </li>
</ul>

*** =hint
data("iris")

*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}

```

*** =solution
```{r}

```

*** =sct
```{r}

```
---








--- type:NormalExercise lang:r xp:100 skills:1 key:427f7df944
## Selecionando uma única variável do dataset

Para a seleção


*** =instructions
22222  dataset que será usado neste exercício chama-se iris, o qual consiste de um tipo de planta com 3 categorias de espécies.

Esta é uma base de dados que já existe no datacamp. O carregamento da base será feito com o uso de uma função chamada data, tendo como argumento o nome do dataset iris

*** =hint
data("iris")

*** =pre_exercise_code
```{r}
data("iris")

```

*** =sample_code
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
## 2222 Multiple Choice Exercise Title

2222 This is the assignment.
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