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

Neste desafio pede-se que selecione do dataset <b>iris</b> o atributo <b>Sepal.Length</b>. E que o resultado desta selação seja armazenado na variável <b>sl</b>

*** =instructions
<ul>
Lembrando que:
 <li>Para saber o nome dos atributos do dataset usa-se a função <span style="font-style:italic;background:#e6f5ff">names()</span></li>
 <li>A seleção de um atributo pode ser feita da seguinte maneira: <span style="font-style:italic;background:#e6f5ff">dataset<b>$</b>atributo</span></li>
</ul>

*** =hint
data("iris")

*** =pre_exercise_code
```{r}
data("iris")
```

*** =sample_code
```{r}
# Selecione do dataset iris o atributo Sepal.Length 
# Salve a seleção na variável sl 
```

*** =solution
```{r}
sl<-iris$Sepal.Length
```

*** =sct
```{r}
test_error()
test_object("sl",
            undefined_msg = "Tem certeza que definiu a variável `sl`!",
            incorrect_msg = "Você atribuiu iris$Sepal.Length a variável `sl`?")
success_msg("Good job! Siga em frente com os desafios de manipulação de dados.")

```
---







--- type:NormalExercise lang:r xp:100 skills:1 key:d8bbb2a3db
## Calculando a média de uma variável
Calcule o valor médio da variável <b>Sepal.Length</b>. E salve o resultado na variável m_sl

*** =instructions
Lembrando que:
<ul>
 <li>A seleção de um atributo pode ser feita da seguinte maneira: <span style="font-style:italic;background:#e6f5ff">dataset$atributo</span></li>
 <li>O cálculo da média pode ser feito com o uso da função <span style="font-style:italic;background:#e6f5ff">mean()</span>. Ela recebe como argumento a sequência de valores que se deseja calcular a média, por exemplo: <span style="font-style:italic;background:#e6f5ff">mean(dataset$atributo)</span></li>
</ul>

*** =hint
data("iris")

*** =pre_exercise_code
```{r}
data("iris")
```

*** =sample_code
```{r}
# Calcule a média do atributo Sepal.Length 
# Salve o resultado na variável m_sl 
```

*** =solution
```{r}
m_sl<-mean(iris$Sepal.Length)
```

*** =sct
```{r}
test_error()
test_object("m_sl",
            undefined_msg = "Tem certeza que definiu a variável `m_sl`!",
            incorrect_msg = "Você atribuiu o resultado da mean(iris$Sepal.Length) a variável `m_sl`?")
success_msg("Good job! Siga em frente com os desafios de manipulação de dados.")

```






--- type:NormalExercise lang:r xp:100 skills:1 key:e5752f2629
## Selecionando os valores do dataset acima da média

Deseja-se saber quais os valores de <b>Sepal.Length</b> estão acima da média. 

*** =instructions
O algoritmo para ter a informação dos maiores valores pode ser descrito como: 

<ul>
 <li>Selecionar o atributo que se deseja manipular (<span style="font-style:italic;background:#e6f5ff">dataset$atributo) e armazenar o resulatdo na variável <b>sl</b></span></li>
 <li>Calcular a média do atributo <span style="font-style:italic;background:#e6f5ff">mean()</span>  e armazenar o resulatdo na variável <b>m_sl</b></li>
 <li>Comparar a sequência de valores com o valor médio. Aqui será preciso fazer uso do operador lógico <b>></b>. Quando se compara <span style="font-style:italic;background:#e6f5ff">sl <b>></b> m_sl</span>, o resultado será uma sequencia de operadores lógicos, representando como TRUE, os valores que satisfazem a condição (maior que a média) e FALSE para o caso contrário.</li>
 <li>Recuperar os valores de <b>Sepal.Length</b> que estão acima da média. Como a resposta da comapração é uma sequência (vetor) lógico, precisamos ter a posição dos elementos que satisfazem a condição (TRUE) para então acessar os valores de Sepal.Length</li>. Para isso faz-se uso da função <span style="font-style:italic;background:#e6f5ff">which()</span>
 <li></li>
</ul>

*** =hint

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