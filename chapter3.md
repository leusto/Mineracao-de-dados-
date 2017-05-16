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





# A impressão dos resulatdos deve ser feia conforme códigos comentados abaixo. Após os cácluos de média e desvio, descomente-os para verificar o resultado.

### DESCOMENTAR CODIGOS APOS CALCULOS DE MEDIA E DESVIO
#resul <- data.frame(Classes=c("setosa", "versicolor", "virginica"),
#                    Média=c(sl_setosa_media, sl_versicolor_media, sl_virginica_media),
#                    Desvio=c(sl_setosa_desvio,sl_versicolor_desvio,sl_virginica_desvio)
#                    )
#print(resul)
####

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
print(resul)
```

*** =sct
```{r}
test_object("resul",
            undefined_msg = "Tem certeza que finalizou o desafio e descomentou o código que tem a variável `resul`!",
            incorrect_msg = "Você tem certeza que calculou a média e o desvio para todas as classes dp atributo `Species`!")
success_msg("Good job! Siga em frente com os desafios de manipulação de dados.")
```



--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:6c83d2ee76
## Interpretando os resultados de média e desvio apresentados no exercício anterior. 

Em relação aos resultados abaixo obtidos do desafio anterior:

     Classes Média    Desvio
1     setosa 5.006 0.3524897
2 versicolor 5.936 0.5161711
3  virginica 6.588 0.6358796


qual das sentenças abaixo, com interpretações dos resulatdos de média e desvio, <b>não é verdadeira</b>:


*** =instructions
- a classe setosa é melhor separada das demais classes
- as classes versicolor e virginica têm valores que se sobrepõem
- a classe setosa tem valores mais coesos em relação as outras classes
- as três classes não apresentam interseção nos valores de Sepal.Lenght

*** =hint
Pense no conceito de média e desvio padrão.

*** =pre_exercise_code
```{r}

```

*** =sct
```{r}
msg1 = "Tente novamente! Note que a média tem valor distinto às outras classes e o desvio não é grande o suficiente para causar sobreposição com as demais classes."
msg2 = "Tente novamente! É uma sentença verdadeira. Embora a média possua valores distintos, o valor do desvio é alto o suficiente para causar sobreposição das classes."
msg3 = "Tente novamente! Verdade, o desvio padrão desta classe é menor que das demais classes."
msg4 = "Well done. As classes tem sim intersesão de classes como será visto no próximo exercício."

test_mc(correct = 4, feedback_msgs = c(msg1,msg2,msg3,msg4))
```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:faf1ec640e
## Entendendo os resultados de média e desvio com uso de explorações gráficas

Ainda analisando o atributo descritivo <b>Sepal.Length</b> e o atributo classificatório <b>Species</b> no sentido de comparar a distribuição dos valores, este exercício consiste na análise de um método gráfico chamado histograma. O gráfico mostra no eixo x os valores do atributo Sepal.Length e a quantidade de vezes que aparece no dataset. A construção será feita com o uso de um pacote chamado ggplo: https://www.rdocumentation.org/packages/ggplot2/versions/2.2.1.

A direita estão dois gráficos gerados, o que ficará incialmente visivel trata-se do histograma para cada classe. Adicionalemnte, clocando no botão Previous Plot, será possível visualizar os histogramas combinados. 

A partir da análise dos dois gráficos, marque a sentença que <b>não é verdadeira</b>:

*** =instructions
- para o atributo analisado, não há sobreposição entre as classes setosa e virginica
- as classes versicolor e virginica têm alto nível de sobreposição
- a classe virgina tem valores mais coesos em relação as outras classes, ou seja, a distribuição é mais concentrada. 
- as três classes apresentam algum grau de interseção nos valores de Sepal.Lenght




*** =hint

*** =pre_exercise_code
```{r}
library(ggplot2)
data("iris")

histogram <- ggplot(data=iris, aes(x=Sepal.Length))
histogram + geom_histogram(binwidth=0.1, color="black", aes(fill=Species)) + 
  xlab("Sepal.Length") +  ylab("Frequencia") + ggtitle("Histograma do atributo Sepal Length")


ggplot(iris, aes(x = iris$Sepal.Length, fill = Species)) +
  geom_histogram(binwidth=0.1,colour = "black") +
  facet_wrap(~ Species) +
  guides(fill = FALSE) +  # to remove the legend
  theme_bw()              # for clean look overall  
  
```

*** =sct
```{r}
msg1 = "Tente novamente! Note que avaliando os histogramas isolados, percebe-se que as classes estão bem separadas."
msg2 = "Tente novamente! É uma sentença verdadeira. Basta olhar para os valores de Sepal Length para ver que há grande sobreposição nos valores."
msg3 = "Well done. Os valores do atributo virginica variam de 5 até 8. A maior coesão aparece para a classe setosa."
msg4 = "Tente novamente! Verdade, veja o gráfico com todos os histogramas plotados."


test_mc(correct = 3, feedback_msgs = c(msg1,msg2,msg3,msg4))
```





--- type:NormalExercise lang:r xp:100 skills:1 key:432f45bba7
## <<<New Exercise>>>


*** =instructions

*** =hint

*** =pre_exercise_code
```{r}
data("iris")
library("ggplot2")
```

*** =sample_code
```{r}

```

*** =solution
```{r}
box <- ggplot(data=iris, aes(x=Species, y=Sepal.Length))
box + geom_boxplot(aes(fill=Species)) + 
  ylab("Sepal Length") + ggtitle("Iris Boxplot") +
  stat_summary(fun.y=mean, geom="point", shape=5, size=4) 
```

*** =sct
```{r}
test_object("box",
            undefined_msg = "Tem certeza que finalizou o desafio e descomentou o código que tem a variável `resul`!",
            incorrect_msg = "Você tem certeza que calculou a média e o desvio para todas as classes dp atributo `Species`!")
success_msg("Good job! Siga em frente com os desafios de manipulação de dados.")
```
--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:bd72cd1f92
## Analisando valores fora do padrão (oulier)


Um valor fora do padrão, também chamado de outlier, consiste em uma medida que foge da distribuição 



*** =instructions

*** =hint

*** =pre_exercise_code
```{r}
ggplot(iris, aes(x = iris$Sepal.Length, fill = Species)) +
  geom_histogram(binwidth=0.1,colour = "black") +
  facet_wrap(~ Species) +
  guides(fill = FALSE) +  # to remove the legend
  theme_bw()              # for clean look overall  
```

*** =sct
```{r}

```
