---
title       : Análise Exploratória dos Dados
description : Este capitulo foca a gamification


--- type:NormalExercise lang:r xp:100 skills:1 key:83990c831d
## Comparando médias

Nos dois últimos exercícios do capítulo anterior vocês foram desafiados a calcular a média e o desvio padrão de uma classe específicao do dataset. Agora, neste exercício, mantendo o atributo descritivo <b>Sepal.Length</b> pede-se que calcule a média e o desvio para todas as classes do dataset, ou seja, <b>setosa</b>,<b>versicolor</b> e <b>virginica</b>.


*** =instructions
Caso não tenha definido a sua própria lógica para selecionar os exemplares de cada classe, segue uma vez mais a opção algortimica: 

<ul>
 <li>Selecionar o atributo que se deseja manipular <b>Species</b></li>
 <li>Comparar a sequência de valores com a classe desejada. 
 <li>Recuperar os indices (posição) dos exemplares que pertencem a classe desejada com a função <span style="font-style:italic;background:#e6f5ff">which()</span>.</li>
</ul>

Com os índices salvos em uma varíavel (que na realidade será um vetor), este deve ser usado para selecionar os exemplares do atributo descritivo <b>Sepal.Length</b>. Ou seja, <span style="font-style:italic;background:#e6f5ff">dataset$atributo[indice]</span>. A partir destes valores calcula-se a média ou o desvio padrão. 



*** =hint
data("iris")

*** =pre_exercise_code
```{r}
data("iris")
```

*** =sample_code
```{r}
# Calcule a média  do atributo Sepal.Length para a classe setosa com o uso da função mean().
# Salve o resultado na variável  sl_setosa_media


# Calcule o desvio  do atributo Sepal.Length para a classe setosa com o uso da função sd().
# Salve o resultado na variável  sl_setosa_desvio


# Calcule a média  do atributo Sepal.Length para a classe versicolor com o uso da função mean().
# Salve o resultado na variável  sl_versicolor_media


# Calcule o desvio  do atributo Sepal.Length para a classe versicolor com o uso da função sd().
# Salve o resultado na variável  sl_versicolor_desvio


# Calcule a média  do atributo Sepal.Length para a classe virginica com o uso da função mean().
# Salve o resultado na variável  sl_virginica_media


# Calcule o desvio  do atributo Sepal.Length para a classe virigina com o uso da função sd().
# Salve o resultado na variável  sl_virginica_desvio





# Imprima o valor como a sequencia de código abaixo:


```

*** =solution
```{r}
sl_setosa<-iris$Sepal.Length[which(iris$Species=="setosa")]
sl_setosa_media <- mean(sl_setosa)
sl_setosa_desvio <- sd(sl_setosa)
#---
sl_versicolor<-iris$Sepal.Length[which(iris$Species=="versicolor")]
sl_versicolor_media <- mean(sl_versicolor)
sl_versicolor_desvio <- sd(sl_versicolor)
#---
sl_virginica<-iris$Sepal.Length[which(iris$Species=="virginica")]
sl_virginica_media <- mean(sl_virginica)
sl_virginica_desvio <- sd(sl_virginica)
#---
resul <- data.frame(Classes=c("setosa", "versicolor", "virginica"),
                    Média=c(sl_setosa_media, sl_versicolor_media, sl_virginica_media),
                    Desvio=c(sl_setosa_desvio,sl_versicolor_desvio,sl_virginica_desvio)
                    )

```

*** =sct
```{r}

```
