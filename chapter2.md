---
title: "Análise Exploratória de Dados"
author: "Prof. Dr. Leandro Augusto"
#date: "20 de fevereiro de 2017"
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```
 <style>
    .exerc-legend{
      background:#e6f5ff;border-top: 2px solid #006bb3;
      }
    .exerc{
      background:#006bb3;color:#fff;padding:5px;
    }
    .enunciado{
      background:#e6f5ff;margin:-10px 0px 0px 15px;padding:10px 0px 20px 0px;border-bottom: 2px solid #006bb3
    }
  </style>
  



O objetivo desta atividade é fazer dois tipos de explorações sob os dados:

1) enriquecer o conjunto de dados (dataset) com o levantamento de metadados como dimensão, tipos de atributos e medidas de resumo;

2) explorar analiticamente o dataset com o uso de estatística descritiva (tendência central, variabilidade) e métodos gráficos para se ter ideias de tipos de análises que podem ser realizadas. Como aqui se trata da primeira aula, a seguir serão definidas algumas propostas de análises com a finalidade de  tornar os estudos mais bem direcionados. Nesse sentido, um case de estudo será definido e apresentado a seguir.


## Case 1: Registros de Batismo do Dr. Arbuthnot

O dataset Arbuthnot refere-se ao resultado de estudo do Dr. John Arbuthnot, médico no século 18, escritor, e matemático que tinha interesse em manter um relatório de recém-nascidos e, por isso, reuniu registros de batismo de crianças nascidas em Londres entre os anos de 1629 a 1710.

A partir deste dataset, algumas análises serão feitas, a fim de se saber:

- quantidade de batizados em cada ano;
- qual sexo tem mais recém-nascidos batizados;
- média de batizados em cada sexo nos anos analisados;
- tendência de batizados (aumento, estacionário ou queda);
- a proporção de batizados meninos e meninas (ou o contrário).

Evidente que outras análises poderiam ser feitas, mas, no entanto, apenas estas serão aqui introduzidas. De toda maneira, em qualquer análise a primeira etapa é a leitura de dados. Sendo assim, a seguir será dado início as análises com a leitura dos dados.


### Leitura e análises iniciais

O conjunto de dados do Dr. Arbuthnot, chamado de 'arbuthnot' estão disponíveis publicamente e podem ser coletados e carregados da seguinte maneira:

```{r}
# Coletando os dados via download
source("http://www.openintro.org/stat/data/arbuthnot.R")
```

Embora não seja um procedimento usual, digitando o nome do dataset no console pode-se ter uma visão completa dos dados:

```{r}
arbuthnot
```


Quando o dataset for muito grande, o procedimento de visão de dados digitando o nome do dataset, como feito antes, não é uma maneira usual, pois pode demandar um processamento que se leva muito tempo. Uma alternativa de visualizar os 6 primeiros registros do dataset pode ser feita da seguinte maneira:

```{r}
head(arbuthnot)
```

O que se deve ver na impressão dos dados são três colunas de números, sendo que  cada linha representa um ano diferente (primeira coluna). A segunda e terceira coluna estão os números de meninos e meninas batizados naquele ano.

Observe que há uma coluna anterior à do ano que não faz parte dos dados do arbuthnot. O R adiciona essa coluna como parte de sua impressão para auxiliar um analista em comparações visuais dos dados. Pode-se pensar nessa coluna como sendo o índice de uma planilha (Excel). De fato, a analogia com uma planilha será geralmente útil, pois o R tem uma estrutura de armazenamento de dados que se assemelha a planilha ou tabela chamada de dataframe.

Agora, iniciando as explorações dos dados com o objetivo de se fazer o enriquecimento do dataset com metados estatísticos, a fim de conhecer melhor a base, é interessante saber, por exemplo, a dimensão do dataset. A dimensão no R é obtida da seguinte maneira:

```{r}
dim_arbuthnot <- dim(arbuthnot)
print(dim_arbuthnot)
```

Aqui a dimensão está sendo armazenada em uma variável para que, caso em uma análise futura, deseja-se ter o controle desses valores.

Como resposta do comando, note que o dataset tem 82 linhas (também chamados na literatura de exemplares, objetos, registros ou instâncias) e 3 colunas (variáveis, atributos, características). 

Em algumas situações, principalmente quando o número de colunas for grande, é importante se ter acesso também ao nome das colunas do dataset, ou seja:


```{r}
colname_arbuthnot <- names(arbuthnot)
print(colname_arbuthnot)
```

Note que o dataframe contém as colunas year, boys e girls. Neste ponto, pode-se perceber que muitos dos comandos em R se assemelham com funções matemáticas; Isto é, invocar comandos R significa fornecer uma função com algum número de argumentos. Os comandos dim e names, por exemplo, exigiram  um único argumento, o nome do dataframe. No decorrer do curso usaremos os termos 'comando' e 'função' indistintamente.

Outra função que é muito útil para rapidamente conhecer o dataset é a str. Esta função mostra de forma compacta a estrutura (STRucture) interna de um objeto R.

```{r}
str(arbuthnot)
```

O enriquecimento com metadados apresentado até o momento é interessante para se ter a dimensão do dataset, o tipo das variáveis, o nome das colunas e uma amostra dos dados. Portanto, o str possibilita uma apresentação completa às opções apresentadas anteriormente. 

Por fim, já caminhando para discutir algumas explorações analíticas do dataset, o comando summary apresenta um resumo estatístico dos dados.

```{r}
summary(arbuthnot)
```

Além de permitir uma primeira análise, o summary permite verificar o intervalo de valores dos dados, importante para algumas tarefas de pré-processamento (discutido em detalhes na próxima aula) como normalização, exitência de valor ausente (não presente aqui nesse dataset) e tipo de distribuição de dados (nesse caso os métodos gráficos facilitam esse tipo de investigação, como será discutido adiante).

Algumas das análises colocadas como objetivos do trabalho já podem ser iniciadas pelo resultado do comando summary. São elas:

- O experimento foi feito entre os anos de 1629 e 1710. Os demais registros de ano não permitem outras análises por se tratar de uma série temporal. Por isso, apenas os valores min e max foram discutidos;
- O menor número de batizados meninos foi de 2890 e o maior 8426. Note que aqui se tem os números, mas não se sabe qual o ano aconteceram. Para isso seria preciso relacionar com a variável year. Adiante na análise gráfica poderá se ter ideia dessas informações; Análise semelhante poderia ser feita para as meninas batizadas;
- A média de meninos batizados nos anos analisados foi de 6073 e a mediana 5907. Aqui se permite ter uma ideia da distribuição dos nascimentos que é de normalidade (média e mediana próximas). Novamente poderia se repetir a análise para as meninas;
- Ordenando o total de nascidos, cerca de 25%, primeiro quartil (1st Qu.), representa um total de 4759 homens; a mediana (segundo quartil) representa 50% e o terceiro quartil (3rd Qu.) representa 75% dos homens batizados. Novamente, analise semelhante poderia ser feita com as meninas;
- Agora, de maneira comparativa, pode-se notar que todas as medidas de boys são maiores que de girls, sugerindo, portanto, um maior número de batizados meninos;

Agora, na seção seguinte, serão apresentadas alguns comandos para manipular os dados e, também, outros tipos de explorações com uso de recursos gráficos;

### Manipulações e explorações do dataset

Note acima que o comanto str trouxe antes do nome de cada coluna o caractere $. O uso desse caractere combinado com o nome do dataset permite que se faça a leitura de uma coluna do dataset. O comando a seguir atribuirá a uma variável o número de meninos batizados:

```{r}
atr_boys<-arbuthnot$boys
print(atr_boys)
```


Alternativamente, a mesma leitura pode ser feita considerando o número da coluna, ou seja,

```{r}
arbuthnot[,2]
```

Aqui, perceba que o número da coluna (2) está dentro do colchete, após o caractere ','. Quando se omite o antecessor a vírgula do colchete, significa que está sendo recuperada toda a coluna, no exemplo, de número 2. O preenchimento com um valor antecedente implicaria em selecionar uma linha específica (ou um conjunto de linhas) para ser selecionada. Por exemplo, para recuperar as primeiras 4 linhas da coluna 2, o seguinte comando deve ser executado:

```{r}
sel_linhas<-arbuthnot[1:4,2]
print(sel_linhas)
```

Analogamente, a mesma maneira de selecionar um conjunto de linhas poderia ser usado para selecionar as colunas.

Agora, analisando quantitativamente a variável numérica atr_boys (tipo esse representado no R por num ou int) é possível usar medidas de tendência central como a média e mediana:

```{r}
media<-mean(atr_boys)
mediana<-median(atr_boys)
print(c(media, mediana))
```

Note que estas medidas já aparecem no summary. Elas foram novamente apresentadas aqui para uso em análises específicas que serão apresentadas no decorrer do curso. Aqui também poderia ser usado a moda (mode), nem sempre útil para medidas numéricas.

Assim como se pode usar as medidas mean e median, em muitas situações é importante também medir as variações das colunas como a variância e o desvio padrão, não mostradas no summary:

```{r}
variancia<-var(atr_boys)
desvio<-sd(atr_boys)
print(c(variancia, desvio))
```

<div class="exerc-legend">
<span class="exerc">Exercícios</span>
</div>

<div class="enunciado">

  1) Calcule a média de meninas batizadas nos 5 primeiros anos da análise do Dr. Arbuthnot. Faça o mesmo para os meninos e compare os resultados.
  
```{r}

```  
  
  2) Apresente o valor mínimo e máximo de meninas batizadas. Repita o mesmo para os meninos e compare os valores.

```{r}
# Dica: as funções min e max retornam os valores mínimos e máximos de uma série de valores

```

</div>



### Explorações gráficas

Para visualizações de dados a biblioteca mais utilizada em R é conhecida como ggplot. Caso se tenha  a biblioteca instalada, então basta iniciá-la para uso:

```{r}
# para caso tenha que instalar o pacote. Este procedimento deve ser feito uma única vez
#install.packages("ggplot")

library(ggplot2)
```

As análises anteriores foram feitas, na maioria dos casos, tratando as variáveis individualmente. A seguir se dará-se início a análises combinando as variáveis. 

O gráfico de dispersão relaciona duas ou mais variáveis. Para o case em questão, seria interessante saber como é a distribuiçõ de batizados por ano. Sendo assim, o comando a seguir representa a construção de um gráfico de dispersão dos recém nascidos homens por ano e, consequentemente, o gráfico será plotado:

```{r}
p<-ggplot(arbuthnot, 
       aes(arbuthnot$year, y = value, color = variable)) + 
       geom_line(aes(y = arbuthnot$boys, col = "boys")) + 
       geom_point(aes(y = arbuthnot$boys, col = "boys")) + 
       scale_color_manual(breaks = c("boys"),
                        values=c("blue"))

p + theme(legend.title=element_blank()) + ggtitle("Batizados") +  labs(x="Ano",y="Número de Batizados")
```


Por este gráfio se pode fazer uma série de análise, por exemplo, no início dos anos em analise, houve uma grande flutuação do número de batizados, depois teve uma queda, atingindo o menor número em 1950 e, depois, voltou a aumentar.  


Contudo, uma curiosidade que surge desta análise é saber como foi a distribuição das meninas. Ou seja, será que o número de batizados das meninas segue a mesma trajetória dos meninos. Para ter este visualização, agora será plotado em um mesmo gráfico o número de meninas e de meninos. Veja a seguir os comandos da plotagem e consequentemente, a figura resultante:



```{r}
p<-ggplot(arbuthnot, 
       aes(arbuthnot$year, y = value, color = variable)) + 
       geom_line(aes(y = arbuthnot$boys, col = "boys")) + 
       geom_point(aes(y = arbuthnot$boys, col = "boys")) +
       geom_line(aes(y = arbuthnot$girls, col = "girls")) +
       geom_point(aes(y = arbuthnot$girls, col = "girls")) + 
       scale_color_manual(breaks = c("boys", "girls"),
                        values=c("blue", "red"))
 
p + theme(legend.title=element_blank()) + ggtitle("Batizados") +  labs(x="Ano",y="Número de Batizados")
  
```

O que é interessante notar no gráfico sobreposto é que o número de meninas batizadas segue exatamente a mesma trajetória dos meninos, porém com um número ligeriamente menor, em todos os anos. Ou seja, o número de meninas batizadas é sempre menor que o de meninos. Esse resultado foi identificado anteriormente com o uso do comando summary que já mostrava que, na média,  o número de batizados meninos era mesmo ligeiramente maior que o de meninas. Os quartis também indicavam a proporção maior em todos os quadrantes. Contudo, aqui com o gráfico, a visualização dessa informação é mais rápida.  

Contudo, os resultados de média e quartis, medidas estatísticas de resumo, são indicadores interessantes e que também podem ser transformados em representações gráficas. O nome desse tipo de plotagem chama-se boxplot e o comando a seguir mostra como este gráfico é elaborado e, consequentemte, o resultado.


```{r}
dat <- data.frame(cond = factor(rep(c("boys","girls"), each=82)), rating = c(arbuthnot$boys,arbuthnot$girls))

p<-ggplot(dat, aes(x=cond, y=rating, fill=cond)) + geom_boxplot() + 
    scale_fill_manual(breaks = c("boys", "girls"),
                        values=c("blue", "red")) +
    stat_summary(fun.y=mean, geom="point", shape=5, size=4)

p + theme(legend.title=element_blank()) + ggtitle("Boxplot") +  labs(x="Sexo",y="Número de Batizados")

```


Cada "caixa" do gráfico tem todas as medidas apresentadas no summary. O valor mínimo e máximo representados aos extremos das linhas verticais que cortam a caixa. A parte de baixo está o segundo quartil, a linha horizontal dentro da caixa a mediana e, na superior, o terceiro quartil. O diamante dentro da caixa representa a média e foi aqui acrescentado para fins de analise de distribuição dos dados. 

Por este gráfico pode-se perceber nitidamente as supeioridades do nascimento em todas as medidas. A posição próxima entre a mediana e média indica a  distrinuição normal dos dados.

De todas as analises colocadas como interesse de descoberta, os resultados acima permitem:

- ter o conhecimento da quantidade de batizados em cada ano através do gráfico de dispersão;
- saber que foram batizados mais homens que mulher, com uso do gráfico de dispersão ou boxplot;
- média de batizados com o uso do comando summary ou pelo uso da função mean;
- ter uma ideia da tendência de nascimento, aparentemente crescente, do número de batizados pelo gráfico de dispersão com as duas variáveis boys e girls;

Contudo, ainda restam algumas analises a serem feitas e que serão deixadas como exercícios.

<div class="exerc-legend">
<span class="exerc">Exercícios</span>
</div>

<div class="enunciado">

1) Qual a proporção de batizados meninos por meninas?

```{r}
# Dica a função sum retorna a somatória de uma sequencia de valores numéricos. 


# O resultado deve ser [1] 1.067294
```

2) Qual ano se nasceu mais meninos? Embora se possa saber dessa informação graficamente, a ideia aqui é que seja feita uma manipulação dos dados para extrair por comandos esta informação. 

```{r}
# Dicas: a função max retorna o máximo valor de uma sequencia numérica; o R permite que se faça comparações lógicas como "==, !=, >,>=, < e <=" em um argumento de função. A resposta dessa comparação será um vetor lógico de TRUE/FALSE. Portanto, para saber os valores que satisfazem a condição, ou seja, o TRUE, pode se usar a função which. Por fim, o indice do valor retornado peo which pode ser usado para manipular uma outra variável.




# O resultado deve ser [1] 1698
```


3) Em qual ano nasceu mais meninas? 

```{r}

```


## Case 2: Planta Iris

A escolha do tipo de gráfico que será utilizado em uma análise depende muito dos atributos do dataset (numérico ou categórico). Como no Case 1 não há atributos categóricos, nos exemplos de análise a seguir o dataset Iris será utilizada. Trata-se de uma base onde através das medidas sob as sépalas e pétalas seja capaz de relacionar ao tipo de planta iris (Setosa, Versicolor ou Virginica). 

O objetivo para este estudo, além de permitir que se aplique os conhecimentos acima de enriquecimento da base com metadados e análises exploratórias e saber, por exemplo:

- É possível ter uma ideia da relevância das medidas feitas na planta no sentido de permitir saber qual a mais efetiva em discernir a espécie da planta Iris?
- A quantidade de plantas é distribuída igualmente para todos as espécies? 


### Leitura e análises iniciais

Como em todo processo de análise, a primeira etapa é sempre feita pela leitura do conjunto de dados (dataset). Como o dataset Iris faz parte do R, a leitura pode ser feita da seguinte maneira:


```{r}
data("iris")
```

Mais adiante outras explorações sobre os dados serão feitas. No entanto, para o momento, faça os exercício a seguir para o enriquecimento de informações e análises iniciais do dataset, assim como feito com arbuthnot:


<div class="exerc-legend">
<span class="exerc">Exercícios</span>
</div>

<div class="enunciado">


1) Qual a dimensão do dataset Iris?

```{r}

```


2) Qual o nome dos atributos presentes no dataset?

```{r}

```

3) Qual o tipo de cada atributo?

```{r}

```

4) Apresente um resumo estatístico do dataset Iris e faça algumas análises em termos de distribuição e intervalo de valores.

```{r}

```

</div>

Após se ter conhecimento dos dados, deseja-se saber a relação de variáveis que são mais representantes para diferenciar os tipos de classes da planta Iris. Para isso, as variáveis podem ser relacionadas aos pares e o comando seguido pelo gráfico estão abaixo representados.


```{r}
p<-ggplot(data=iris, 
       aes(iris$Sepal.Length, y = iris$Sepal.Width, color = iris$Species)) + 
       geom_point() 
 
p + theme(legend.title=element_blank()) + ggtitle("Iris Dataset") +  labs(x="Sepal.Lenght",y="Sepal.Width")
```


Note por este gráfico que a representação do dataset pelas variáveis Sepal.Width e Sepal.Lenght permite separar muito bem a classe Setosa, mas não ocorre o mesmo para as classes Versicolor e Virginica.

Para que está mesma análise não seja feita combinando todos os atributos a seguir, deixando momentaneamente de lado a biblioteca ggplot2 (será notado pela perda de qualidade), o comando e gráficos mostram a combinação de plotagem de todas as variáveis aos pares, em gráficos em uma estrtura de matriz. A dimensão da matriz é formada pelo número de atributos do dataset e a combinação entre linhas e colunas mostra a relevância da combinação a cada duas variáveis. Em suma, o que se pode ver é que em todas as combinações sempre uma classe separa-se bem das demais que é justamente a setosa (mapeada no gráfico abaixo na cor preta, com codificação 1, sendo a codificação feita pela ordem alfabética do nome das classes).


```{r}
plot(iris,col=iris$Species)
```



De forma complementar aos resultados acima, o gráfico a seguir mostra a distribuição de um dos atributos, Sepal.Length, em função da classe da planta iris. Esse gráfico tem no eixo x os valores da medida Sepal.Length e no y a quantidade de vezes que cada valor aparece (densidade). O que é interessante notar nesse resultado gráfico é que a medida é mais representativa (ou discriminante como definiremos adiante) para a classe setosa, havendo então uma sobreposição as demais classes. Informação já conhecida antes, porém aqui com uma menor granularidade em termos numérios com o valor de onde as sobreposições começaam a aparecer


```{r}
p<-ggplot(iris, aes(iris$Sepal.Length)) + geom_density(aes(fill = iris$Species))
p + theme(legend.title=element_blank())  + ggtitle("Densidade da variável Sepal.Lenght") +  labs(x="Sepal.Lenght",y="Densidade")
```


Como análise final, é interessante saber se a quantidade de classes está distribuida igualmente ou se há desbalanceamento de classes. Essa informação é importante para estudos futuros sobre análise preditiva. Para se ter esta informação, um tipo de medida bastante comum para dados categórico é o gráfico de setores (ou pizza). O comando a seguir e o consecutivo gráfico mostram o resultado da distribuição das classes da planta Iris no dataset. 

```{r}
p<-ggplot(iris, aes(x = " ", y = " ", fill = iris$Species)) +
 geom_bar(width = 1, stat="identity") +
 coord_polar("y") 
p + theme(legend.title=element_blank()) + ggtitle("Quantidade de Classes") +  labs(x="",y="")
```

Nota-se por este gráfico que há um balanceamento entre todas as classes, ou seja, o mesmo número objetos para cada Species. 

Como discussão final desta aula, é importante ficar claro que os dois cases aqui apresentados permitem explorar uma parte do conjunto gráfico que se tem na literatura para análise exploratória de dados. Assim, outros tipos serão apresentados no decorrer do curso. E ainda, é importante enfatizar que estas análises tem importância muito mais ampla que a de retirar ideias sobre os dados. Elas também são úteis para verificar necessidades de pre-processamento de dados e, ainda mais importante, permitir que se entenda algum tipo de comportamento, como por exemplo, saber que um modelo preditivo terá dificuldades de separar as classes Versicolor e Virgínica do dataset Iris.