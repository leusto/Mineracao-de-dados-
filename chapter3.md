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
## Analisando valores fora do padrão (oulier)

Um valor fora do padrão, também chamado de outlier, consiste em uma medida que extrapola os limites estabelecitos pelos quartis dos valores dos dados. A identificação desse valor pode ser feita com o uso do boxplot, gráfico que aparece ao lado. 

Para um entendimento detalhado do significado deste gráfico, recomenda-se a leitura do capítulo 2 da seguinte literatura:<a href="https://www.amazon.com.br/Introdu%C3%A7%C3%A3o-Minera%C3%A7%C3%A3o-Dados-Leandro-Augusto/dp/853528446X/ref=cm_cr_arp_d_product_top?ie=UTF8">Introdução a Mineração de Dados</a>.

Para esta atividade, o que interessa é identificar nos gráficos de boxplot se para o atributo descritivo Sepal.Length, separado por atributos classificatórios, há algum ponto fora das barras paralelas que indicam os limites toleráveis de valores dentro de um padrão esperado.


*** =instructions
Para a solução desta atividade, atribua a uma variável chamada resposta, o nome do atributo classificatório com problema de outlier.

*** =hint

*** =pre_exercise_code
```{r}
data("iris")
library("ggplot2")
ggplot(data=iris, aes(x=Species, y=Sepal.Length)) + geom_boxplot(aes(fill=Species)) + ylab("Sepal Length") + ggtitle("Iris Boxplot") + stat_summary(fun.y=mean, geom="point", shape=5, size=4)
```

*** =sample_code
```{r}
# Geração do Box Plot para o atributo descritivo  Sepal.Length
ggplot(data=iris, aes(x=Species, y=Sepal.Length)) + geom_boxplot(aes(fill=Species)) + ylab("Sepal Length") + ggtitle("Iris Boxplot") + stat_summary(fun.y=mean, geom="point", shape=5, size=4)

# atribua a variável resposta o nome do atributo classificatório com outlier

```

*** =solution
```{r}
resposta <- "virginica"
```

*** =sct
```{r}
test_error()
test_object("resposta",
            undefined_msg = "Tenha certeza da declaração da variável  `resposta`!",
            incorrect_msg = "O atributo classificatório definido está icorreto. Verifique qual gráfico de boxplote tem a presença de um ponto fora das linhas verticais. ")
success_msg("Good job! SIga em frente com o próximo desafio para identificar o atributo com outlier")
```






--- type:NormalExercise lang:r xp:100 skills:1 key:b28917e5a0
## Identificando a posição do valor com oulier 

A inspeção visual oferece um recurso interessante para verificar a existência de um oulier. No entanto, mais importante que saber da existência dessa anomalia, é importante a identificação do mesmo. Esta atividade tem como finalidade identificar a posição do exemplar com o problema de oulier. 


*** =instructions

O algoritmo que possibilita identifica o outlier é semelhante aos utilizados antes com uso do operador lógico para comparação e função $which()$ para descobrir a posição. 

O algoritmo para ter os exemplares da classe <b>setosa</b> com outlier pode ser descrito como: 

<ol>
 <li>Selecionar o atributo que se deseja manipular $dataset$atributo$ e armazenar o resulatdo na variável <b>classes</b></span></li>
 <li>Comparar a sequência de valores com a classe desejada <b>setosa</b>. Aqui será preciso fazer uso do operador lógico <b>==</b>. Quando se compara $classes<b>==</b>"virginica"$, o resultado será uma sequencia de operadores lógicos, representando como TRUE, os valores que satisfazem a condição (igual) e FALSE para o caso contrário.</li>
 <li>Recuperar os indices (posição) dos exemplares que pertencem a classe <b>virginica</b>. Como a resposta da comparação é uma sequência (vetor) lógico, precisamos ter a posição dos elementos que satisfazem a condição (TRUE) para então acessar os valores de setosa. Para isso faz-se uso da função $which()$. Essa função recebe como parâmetro os valores lógicos e retorna a posição em que aparece a condição TRUE. </li>
 <li>Usar os indices para recuperar o valor dos exemplares, por exemplo, $dataset$atributo[indices]$</li>
 <li>Analisar o gráfico identificar o valor de outlier e fazer a comparação, como no segundo passo desse algortimo.</li>
 <li>Identificar os valores, seguindo procedimento semelhante ao descrito nos passos 3 e 4</li>
</ol>


*** =hint

*** =pre_exercise_code
```{r}
data("iris")
library("ggplot2")

classes <- iris$Species
classes_setosa <- iris$Species=="virginica"
classes_setosa_ex <- which(classes_setosa==TRUE)
data_2<-as.data.frame(iris$Sepal.Length[classes_setosa_ex])

box_virginica <- ggplot(data_2, aes(x="virginica", y=data_2)) + 
  geom_boxplot(aes(fill="virginica")) + 
  ylab("Sepal Length") + ggtitle("Iris Boxplot") + scale_fill_manual(values=c(rgb(0, 0.8, 1)))

```

*** =sample_code
```{r}
# Selecione do dataset iris o atributo Species 
# Salve o resultado na variável classes


# Compare a sequencia de valores classes iguais a virginica
# Salve o resultado na variável classes_virginica



# Recupere a posição (indices) dos exemplares que pertencem a classe virginica
# Salve na variável 'classes_virginica_ex'


# Use a variavel 'classes_virginica_ex' como indice de iris$Sepal.Length 
# e compare com valores < a 5.5
# Salve o resultado na variavel outlier


# A variavel oulier é um vetor de bolleano. Para pegar os valores TRUE, ou seja,
# que satisfazem a condição (< 5.5), use a função which()
# Salve o resultado na variavel outlier_indice



# O resultado da variável outlier_indice deve ser usado como indice classes_setosa_ex.
# Salve o resultado na variável outlier_ex



# Imprima o valor da variável 'outlier_ex'

```

*** =solution
```{r}
classes <- iris$Species
classes_virginica <- iris$Species=="virginica"
classes_virginica_ex <- which(classes_virginica)
outlier <- iris$Sepal.Length[classes_virginica_ex] < 5.5
outlier_indice <- which(outlier)
outlier_ex <- classes_setosa_ex[outlier_indice]
print(outlier_ex)
```

*** =sct
```{r}
test_error()
test_object("outlier_ex",
            undefined_msg = "Tenha certeza que foi feita a declaração da variável  `outlier_ex`!",
            incorrect_msg = "O resultado da variável `outlier_ex` está icorreto. Verifique os passos do algoritmo explicados em `instructions`. ")
success_msg("Good job! Perceba que o valor identificado é o mesmo que aparecia distânte da distribuição da variável virginica.")
```
