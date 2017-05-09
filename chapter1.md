
--- type:NormalExercise lang:r xp:100 skills:1 key:427f7df944
## Este exercício consiste em carregar um dataset e fazer algumas explorações iniciais sobre os mesmos


*** =instructions
O dataset que será usado neste exercício chama-se iris, o qual consiste de um tipo de planta com 3 categorias de espécies.)

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