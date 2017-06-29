---
title       : Manipulando o dataset
description : Este capitulo consiste em realizar algumas maninpualções do dataset como selecionar uma variável, calcular a média, calcular o desvio de uma variável e desenvolver desafios gráficos como a geração do boxplot, gráfico de dispersao e de histograma.

--- type:NormalExercise lang:r xp:100 skills:1 key:66f49495b2
## Selecionando um único atributo do dataset

A seleção de um único atributo do dataset pode ser feito agrupando ao nome do dataset o nome do atributo de interesse. O operador de agrupamento no R  é o <b>$</b>.

Neste desafio pede-se que selecione do dataset <b>iris</b> o atributo <b>Sepal.Length</b>. E que o resultado desta selação seja armazenado na variável <b>sl</b>

*** =instructions
<ul>
Lembrando que:
 <li>Para saber o nome dos atributos do dataset usa-se a função *names()*</li>
 <li>A seleção de um atributo pode ser feita da seguinte maneira: *dataset$nome_atributo*</li>
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
            undefined_msg = "Verifique se declarou a variável `sl`!",
            incorrect_msg = "Verifique se atribuiu iris$Sepal.Length a variável `sl`")
success_msg("Good job! Siga em frente com os desafios de manipulação de dados.")

```
---







--- type:NormalExercise lang:r xp:100 skills:1 key:d8bbb2a3db
## Calculando a média de uma variável
Calcule o valor médio da variável <b>Sepal.Length</b>. E salve o resultado na variável m_sl

*** =instructions
Lembrando que:
<ul>
 <li>Para saber o nome dos atributos do dataset usa-se a função *names()*;</li>
 <li>O cálculo da média pode ser feito com o uso da função *mean()*. A função recebe como parâmetro a sequência de valores que se deseja calcular a média, por exemplo: *mean(dataset$atributo).</li>
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
            undefined_msg = "Verifique se definiu a variável `m_sl`!",
            incorrect_msg = "Verifique se atribuiu o resultado da mean(iris$Sepal.Length) a variável `m_sl`?")
success_msg("Good job! Siga em frente com os desafios de manipulação de dados.")

```






--- type:NormalExercise lang:r xp:100 skills:1 key:e5752f2629
## Selecionando valores do dataset acima da média

Deseja-se saber neste desafio quais os valores de <b>Sepal.Length</b> estão acima da média. 

*** =instructions
O algoritmo para ter a informação dos maiores valores pode ser descrito como: 

<ul>
 <li>Selecionar o atributo que se deseja manipular (*dataset$nome_atributo*) e armazenar o resulatdo na variável <b>sl</b></li>
 <li>Calcular a média do atributo com uso da função *mean()*  e armazenar o resulatdo na variável <b>m_sl</b></li>
 <li>Comparar a sequência de valores com o valor médio. Aqui será preciso fazer uso do operador lógico <b>></b>. Quando se compara <span style="font-style:italic;background:#e6f5ff">sl <b>></b> m_sl</span>, o resultado será uma sequencia de operadores lógicos, atribuindo como TRUE os valores que satisfazem a condição (maior que a média) e FALSE ao caso contrário.</li>
 <li>Recuperar os índices (posição na sequência de valores) de <b>Sepal.Length</b> que estão acima da média. Como a resposta da comapração é uma sequência (vetor) lógico, precisamos ter a posição dos elementos que satisfazem a condição (TRUE) para então acessar os valores de Sepal.Length. Para isso faz-se uso da função *which()*. Essa função recebe como parâmetro os valores lógicos e retorna a posição em que a condição TRUE acontece. </li>
 <li>Recuperar os valores de <b>Sepal.Length</b> que estão acima da média. O resulatdo da função *which()* é usado como índice para a recuperação dos valores de Sepal.Length. O indíce será usado como valor do colchetes <span style="font-style:italic;background:#e6f5ff">[ ]</span> agregado ao dataset e atributo, como no exemplo: <span style="font-style:italic;background:#e6f5ff">dataset$atributo[índice]</span> </li>
</ul>

*** =hint
data("iris")

*** =pre_exercise_code
```{r}
data("iris")
```

*** =sample_code
```{r}
# Selecione o atributo Sepal.Length do dataset iris 
# Salve o resultado na variável sl


# Calcule e média do atributo Sepal.Length
# Salve o resultado na variável sl_m



# Compare a sequência com o valor médio para ter os maiores valores
# Salve o resultado na variável 'maiores'


# Recupere a posição (indices) dos valores de Sepal.Length que são maiores que a média
# Salve na variável 'indices'


# Imprima os valores dos indices com a função print()


# Recupere os valores de Sepal.Length que estão acima da média
# Salve na variável 'sl_acima_media'


# Imprima os valores de sl_acima_media com a função print()

```

*** =solution
```{r}
sl_acima_media<-iris$Sepal.Length[indices]
```

*** =sct
```{r}
test_error()
test_object("sl_acima_media",
            undefined_msg = "Verifique se definiu a variável `sl_acima_media`!",
            incorrect_msg = "Verifique se todos os passos do algoritmo apresentados em `instructions` foram seguidos?")
success_msg("Good job! Siga em frente com os desafios de manipulação de dados.")

```
--- type:NormalExercise lang:r xp:100 skills:1 key:427f7df944
## Manipulando a variável categorica do dataset

A coluna <b>Species</b> refere-se ao atributo categorico do dataset. É por meio dela que se classifica (ou rotula) os exemplares da planta Iris. Deseja-se saber quais os tipos de plantas Iris existem no dataset.


*** =instructions
Aqui deseja-se basicamente que seja selecionado o atributo <b>Species</b>, nos mesmos moldes do que feito antes com o atributos Sepal.Length e imprima o resultado para se conhecer os tipos disponpiveis no dataset.

*** =hint
data("iris")

*** =pre_exercise_code
```{r}
data("iris")

```

*** =sample_code
```{r}
# recuperar os valores do atributo Species e salvá-los na variável classes

# imprimir os valores da variável 'classes'
```

*** =solution
```{r}
classes<-iris["Species"]
```

*** =sct
```{r}
test_error()
test_object("classes",
            undefined_msg = "Verifique se definiu a variável `classes`!",
            incorrect_msg = "Verifique se selecionou apenas o atributo Species para `classes`!")
success_msg("Good job! Siga em frente com os desafios de manipulação de dados.")

```
---



--- type:MultipleChoiceExercise lang:r xp:50 skills:3 key:e74c30a746
## Em relação às espécies da planta Iris: 

Qual o total de classes presentes no dataset?

*** =instructions
- 2
- 3
- 4
- 150

*** =hint
Pense sobre os tipos possóveis de classes e não do total de exemplares no dataset.

*** =pre_exercise_code
```{r}
# no pec
```

*** =sct
```{r}
msg1 = "Tente novamente! Pense sobre o número de classes."
msg2 = "Well done. Continue com os exercícios"
msg3 = "Tente novamente! Pense sobre o número de classes."
msg4 = "Tente novamente! Pense sobre o número de classes e não o total de exemplares."

test_mc(correct = 2, feedback_msgs = c(msg1,msg2,msg3,msg4))
```


--- type:NormalExercise lang:r xp:100 skills:1 key:ddb49a486b
## Selecionando os exemplares de uma classe específica

O desafio deste exercício é recuperar apenas os exemplares da classe <b>setosa</b>. A solução é muito parecida com o que feito antes sobre a seleção dos valores de Sepal.Length acima da média. A diferença aqui é que o operador de comparação a ser usado é o igual (<b>==</b>). 


*** =instructions
O algoritmo para ter os exemplares da classe  <b>setosa</b> pode ser descrito como: 

<ul>
 <li>Selecionar o atributo que se deseja manipular (<span style="font-style:italic;background:#e6f5ff">dataset$nome_atributo</span>) e armazenar o resulatdo na variável <b>classes</b></span></li>
 <li>Comparar a sequência de valores com a classe desejada <b>setosa</b>. Aqui será preciso fazer uso do operador lógico <b>==</b>. Quando se faz a comparação <span style="font-style:italic;background:#e6f5ff">classes<b>==</b>"setosa"</span>, o resultado será uma sequência de operadores lógicos, representando como TRUE os valores que satisfazem a condição (igual) e FALSE ao caso contrário.</li>
 <li>Recuperar os índices (posição) dos exemplares que pertencem a classe <b>setosa</b>. Como a resposta da comparação é uma sequência (vetor) lógico, precisa-se ter a posição dos elementos que satisfazem a condição (TRUE) para então acessar os valores de setosa. Para isso faz-se uso da função *which()*. Essa função recebe como parâmetro os valores lógicos e retorna a posição em que aparece a condição TRUE. </li>
</ul>


*** =hint
data("iris")

*** =pre_exercise_code
```{r}
data("iris")
```

*** =sample_code
```{r}
# Selecione do dataset iris o atributo Species 
# Salve o resultado na variável classes


# Compare a sequência de valores classes iguais a setosa
# Salve o resultado na variável classes_setosa




# Recupere a posição (índices) dos exemplares que tem pertencem a classe setosa
# Salve na variável 'classes_setosa_ex'



# Imprima o valor da variável 'classes_setosa_ex'


```

*** =solution
```{r}
classes <- iris$Species
classes_setosa <- iris$Species=="setosa"
classes_setosa_ex <- which(classes_setosa)
```

*** =sct
```{r}
test_error()
test_object("classes_setosa_ex",
            undefined_msg = "Verifique se definiu corretamente a variável `classes_setosa_ex`!",
            incorrect_msg = "Verifique se selecionou apenas o atributo Species para `classes`!")
success_msg("Good job! Siga em frente com os desafios de manipulação de dados.")
```


--- type:NormalExercise lang:r xp:100 skills:1 key:f97586016a
## Juntando os atributos <i>Sepal.Length</i> e <i>Species</i>

O objetivo deste desafio é combinar os exercícios anteriores em uma única atividade que é o calculo da média dos exemplares do atributo descritivo <b>Sepal.Length</b> que pertencem a classe <b>setosa</b>. 


*** =instructions
O algoritmo para selecionar os exemplares da classe <b>setosa</b> deve ser usado integralmente nesta atividade, ou seja: 

<ul>
 <li>Selecionar o atributo que se deseja manipular <b>Species</b></li>
 <li>Comparar a sequência de valores com a classe desejada <b>setosa</b>. 
 <li>Recuperar os indices (posição) dos exemplares que pertencem a classe <b>setosa</b> com a função <span style="font-style:italic;background:#e6f5ff">which()</span>.</li>
</ul>

Com os índices salvos em uma varíavel (que na realidade será um vetor), deve-se usá-lo para selecionar os exemplares do atributo descritivo <b>Sepal.Length</b>. Ou seja, <span style="font-style:italic;background:#e6f5ff">dataset$atributo[indice]</span>. A partir destes valores calcula-se a média. 


*** =hint
data("iris")

*** =pre_exercise_code
```{r}
data("iris")
```


*** =sample_code
```{r}
# Selecione do dataset iris o atributo Species 
# Salve o resultado na variável classes


# Compare a sequencia de valores classes iguais a setosa
# Salve o resultado na variável classes_setosa




# Recupere a posição (indices) dos exemplares que tem pertencem a classe setosa
# Salve na variável 'classes_setosa_ex'


# Recupere do dataset iris o atributo Sepal.Length
# Salve na variável 'sl'


# Selecione da variável sl apenas os exemplares que pertencem a classe setosa (classes_setosa_ex)
# Salve na variável sl_setosa


# Calcule a média da variável sl_setosa com o uso da função mean().
# Salve o resultado na variável  sl_setosa_media


# Imprima o valor da variável sl_setosa_media

```

*** =solution
```{r}
classes <- iris$Species
classes_setosa <- iris$Species=="setosa"
classes_setosa_ex <- which(classes_setosa)
sl <- iris$Sepal.Length
sl_setosa <- sl[classes_setosa_ex]
sl_setosa_media <- mean(sl_setosa)
```

*** =sct
```{r}
test_object("sl_setosa_media",
            undefined_msg = "Verifique se definiu a variável `sl_setosa_media`!",
            incorrect_msg = "Verifique se selecionou apenas os exemplares da classe `setosa`!")
success_msg("Good job! Siga em frente com os desafios de manipulação de dados.")
```



--- type:NormalExercise lang:r xp:100 skills:1 key:6909085486
## Calculando o desvio padrão

A ideia desta atividade é repetir todo o exercício anterior, porém ao invés de calcular a média, deseja-se calcular o desvio padrão


*** =instructions

O desvio padrão é calculado com o uso da função *sd()*.

*** =hint

*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}
# Selecione do dataset iris o atributo Species 
# Salve o resultado na variável classes


# Compare a sequencia de valores classes iguais a setosa
# Salve o resultado na variável classes_setosa




# Recupere a posição (índices) dos exemplares que tem pertencem a classe setosa
# Salve na variável 'classes_setosa_ex'


# Recupere do dataset iris o atributo Sepal.Length
# Salve na variável 'sl'


# Selecione da variável sl apenas os exemplares que pertencem a classe setosa (classes_setosa_ex)
# Salve na variável sl_setosa


# Calcule o desvio da variável sl_setosa com o uso da função sd().
# Salve o resultado na variável  sl_setosa_desvio


# Imprima o valor da variável sl_setosa_desvio
```

*** =solution
```{r}
classes <- iris$Species
classes_setosa <- iris$Species=="setosa"
classes_setosa_ex <- which(classes_setosa)
sl <- iris$Sepal.Length
sl_setosa <- sl[classes_setosa_ex]
sl_setosa_desvio <- sd(sl_setosa)
```

*** =sct
```{r}
test_object("sl_setosa_desvio",
            undefined_msg = "Verifique se definiu a variável `sl_setosa_desvio`!",
            incorrect_msg = "Verifique se selecionou apenas os exemplares da classe `setosa`!")
success_msg("Good job! Siga em frente com o próximo capítulo de atividades.")
```
