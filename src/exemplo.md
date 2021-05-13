Bucket Sort 
======

Gabriela Mitu | Gabriella Cukier | Henrique Mualem

Ideia do Algortimo
---------

Um algoritmo de classificação é usado para reorganizar uma determinada matriz ou elementos de lista de acordo com um operador de comparação nos elementos. O operador de comparação é usado para decidir a nova ordem do elemento na respectiva estrutura de dados.
Existem muitos algoritmos de classificação diferentes, com vários prós e contras. Nesse Handout iremos focar no algoritmo **Bucket Sort**.


Vamos começar imaginando uma situação hipotética
Um belo dia, você encontrou um jogo de BINGO e resolveu ordenar as bolas em ordem crescente para armazená-las de forma organizada. No jogo existem 75 bolas. Ordená-las diretamente levaria muito tempo, mas você percebeu que tinha 5 pequenos baldes à disposição.


![](bingo.png)

??? Checkpoint

De que maneira poderíamos utilizar esses baldes para tornar a ordenação mais rápida?

::: Gabarito
Poderíamos estabelecer cada balde como um intervalo numérico. Como existem 75 bolas e 5 baldes, cada balde teria ao final da ordenação 15 bolas. No primeiro, colocaríamos as bolas de 1 a 15, no segundo, as bolas de 16 a 30 e assim por diante. Desse modo, ao final teríamos apenas que organizar os baldes individualmente. Concatenando as bolas dos baldes em ordem crescente teríamos então o resultado ordenado desejado.
:::

???


Essa é a ideia fundamental do Bucket Sort. A entrada a ser ordenada, um array, é dividida em intervalos (os chamados “baldes”), que, então, são ordenados separadamente e, após concatenados, resultam na saída, correspondente ao array de entrada agora ordenado.
A grande vantagem do algoritmo é que cada balde pode ser processado independentemente dos outros e de forma paralela. 

Funcionamento em Detalhes
---------

O mais comum é o Bucket Sort ser implementado na forma de função, que recebe um array e um número de intervalos (n) que serão utilizados para a ordenação. 
A implementação pode ser feita em quatro passos:
1. Criação dos n baldes (inicializados como listas vazias)
2. Inserção dos elementos em seus respectivos baldes - a posição em que o elemento do array será inserido é definida por index = n*array[i]
3. Ordenar cada balde separadamente
4. Concatenar os conteúdos de todos os baldes em ordem crescente

Mas como exatamente ocorre essa ordenação dentro de cada balde do passo 3? 
Podemos utilizar uma versão recursiva do Bucket Sort ou então algum outro algoritmo de ordenação.



1. listas;

2. ordenadas,

assim como

* listas;

* não-ordenadas

e imagens. Lembre que todas as imagens devem estar em uma subpasta *img*.



Para tabelas, usa-se a [notação do
MultiMarkdown](https://fletcher.github.io/MultiMarkdown-6/syntax/tables.html),
que é muito flexível. Vale a pena abrir esse link para saber todas as
possibilidades.

| coluna a | coluna b |
|----------|----------|
| 1        | 2        |

Ao longo de um texto, você pode usar *itálico*, **negrito**, {red}(vermelho) e
[[tecla]]. Também pode usar uma equação LaTeX: $f(n) \leq g(n)$. Se for muito
grande, você pode isolá-la em um parágrafo.

$$\lim_{n \rightarrow \infty} \frac{f(n)}{g(n)} \leq 1$$

Para inserir uma animação, use `md ;` seguido do nome de uma pasta onde as
imagens estão. Essa pasta também deve estar em *img*.

;bucket

Você também pode inserir código, inclusive especificando a linguagem.

``` py
def f():
    print('hello world')
```

``` c
void f() {
    printf("hello world\n");
}
```

Se não especificar nenhuma, o código fica com colorização de terminal.

```
hello world
```


!!! Aviso
Este é um exemplo de aviso, entre `md !!!`.
!!!


